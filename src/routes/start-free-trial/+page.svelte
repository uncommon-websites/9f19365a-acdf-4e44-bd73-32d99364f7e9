<script lang="ts">
	// Icons
	const Check = `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>`;
	const ChevronLeft = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6"/></svg>`;
	const Lock = `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>`;
	const CreditCard = `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="14" x="2" y="5" rx="2"/><line x1="2" x2="22" y1="10" y2="10"/></svg>`;

	// Form state
	let currentStep = $state(1);
	let formData = $state({
		firstName: '',
		lastName: '',
		email: '',
		password: '',
		selectedPlan: 'professional',
		cardNumber: '',
		cardExpiry: '',
		cardCvc: '',
		cardName: ''
	});

	// Validation
	let errors = $state<Record<string, string>>({});

	function validateStep1() {
		const newErrors: Record<string, string> = {};
		
		if (!formData.firstName.trim()) newErrors.firstName = 'First name is required';
		if (!formData.lastName.trim()) newErrors.lastName = 'Last name is required';
		if (!formData.email.trim()) {
			newErrors.email = 'Email is required';
		} else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
			newErrors.email = 'Please enter a valid email';
		}
		if (!formData.password) {
			newErrors.password = 'Password is required';
		} else if (formData.password.length < 8) {
			newErrors.password = 'Password must be at least 8 characters';
		}

		errors = newErrors;
		return Object.keys(newErrors).length === 0;
	}

	function validateStep2() {
		const newErrors: Record<string, string> = {};
		
		if (!formData.cardNumber.trim()) newErrors.cardNumber = 'Card number is required';
		if (!formData.cardExpiry.trim()) newErrors.cardExpiry = 'Expiry date is required';
		if (!formData.cardCvc.trim()) newErrors.cardCvc = 'CVC is required';
		if (!formData.cardName.trim()) newErrors.cardName = 'Cardholder name is required';

		errors = newErrors;
		return Object.keys(newErrors).length === 0;
	}

	function handleNext() {
		if (validateStep1()) {
			currentStep = 2;
			errors = {};
		}
	}

	function handleBack() {
		currentStep = 1;
		errors = {};
	}

	function handleSubmit() {
		if (validateStep2()) {
			// Here you would submit to your backend
			console.log('Form submitted:', formData);
			alert('Trial started! (This is a demo)');
		}
	}

	const plans = [
		{
			id: 'starter',
			name: 'Starter',
			price: 79,
			clients: 'Up to 15 active clients',
			features: [
				'Full platform access with AI-assisted program design',
				'Unified calendar for training, nutrition, and lifestyle',
				'Client mobile app, messaging, and compliance tracking',
				'Free migration and onboarding support'
			]
		},
		{
			id: 'professional',
			name: 'Professional',
			price: 149,
			clients: 'Up to 40 active clients',
			popular: true,
			features: [
				'Everything in Starter, plus advanced analytics',
				'Wearable integrations and biometric tracking',
				'Stripe billing integration and storefront creation',
				'Priority support and OPEX education discounts'
			]
		}
	];
