<script lang="ts">
	import { onMount } from 'svelte';

	// Icons
	const ChevronRight = `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>`;
	const ChevronLeft = `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6"/></svg>`;
	const PlayCircle = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polygon points="10 8 16 12 10 16 10 8"/></svg>`;
	const Plus = `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="M12 5v14"/></svg>`;
	const Check = `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>`;
	const Instagram = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="20" x="2" y="2" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" x2="17.51" y1="6.5" y2="6.5"/></svg>`;
	const Linkedin = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect width="4" height="12" x="2" y="9"/><circle cx="4" cy="4" r="2"/></svg>`;
	const XIcon = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 6 6 18"/><path d="m6 6 18 18"/></svg>`;

	let faqs = [
		{ question: "How does CoachRx help me scale my coaching business?", open: false },
		{ question: "Can I migrate my existing clients from Excel or other platforms?", open: false },
		{ question: "What makes CoachRx different from TrueCoach or Trainerize?", open: false },
		{ question: "Do I need to be OPEX certified to use CoachRx?", open: false },
		{ question: "How does the AI assistant (RxBot) work?", open: false }
	];

	function toggleFaq(index: number) {
		faqs = faqs.map((faq, i) => {
			if (i === index) return { ...faq, open: !faq.open };
			return faq;
		});
	}
</script>

<div class="min-h-screen flex flex-col font-sans text-gray-900 bg-[#FAFAFA]">
	<!-- Top Banner -->
	<div class="bg-black text-white text-[11px] font-medium py-3 text-center tracking-wide px-4">
		Start your 14-day free trial today. Full access to all features, no credit card required.
	</div>

	<!-- Navigation -->
	<nav class="flex items-center justify-between px-6 md:px-12 py-5 bg-[#FAFAFA]">
		<div class="flex items-center gap-2">
			<!-- Logo -->
			<div class="flex items-center gap-2">
				<div class="w-6 h-6 text-black">
					<svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path
							fill-rule="evenodd"
							clip-rule="evenodd"
							d="M5.0473 17.8386L5.69453 18.9586V18.9601H18.3003L18.9314 17.84H6.34063L6.82626 16.9993H19.4308L20.078 15.8807H7.47237L7.95715 15.0414H16.0358L16.0366 15.0429L16.0375 15.0414H20.5603L20.5612 15.0429L21.2084 13.9228L21.208 13.922L21.2084 13.9213H21.2075L14.9084 3.00677L14.9106 3.00296L14.9062 3.00296L13.6177 3.00296L5.0473 17.8386ZM14.261 4.12767L13.7751 4.96887L18.9438 13.9213H19.9139L14.261 4.12767ZM13.1286 6.08808L12.6467 6.9225L16.6749 13.9006L16.6634 13.9213H17.6511L13.1286 6.08808ZM11.9999 8.04225L8.60411 13.9213H15.3899L11.9999 8.04225ZM6.99833 3.30006C7.33866 3.10343 7.7248 2.99993 8.11786 3L2.30033 13.0776C2.10357 12.7371 2 12.3508 2 11.9575C2 11.5643 2.10357 11.178 2.30033 10.8375L6.17916 4.12006C6.37543 3.77951 6.65798 3.49669 6.99833 3.30006ZM9.08869 3H10.3816L3.43223 15.0384L2.785 13.9184L9.08869 3ZM11.3509 3H12.6424L4.56262 16.9963L3.91691 15.8777L11.3509 3ZM21.7064 13.0598C21.8988 12.7254 22 12.3463 22 11.9605C22 11.5746 21.8988 11.1956 21.7064 10.8611L17.8039 4.10233C17.6108 3.7681 17.3331 3.49057 16.9987 3.2976C16.6644 3.10463 16.2852 3.00302 15.8992 3.00296H15.8741L21.6931 13.082L21.7064 13.0598ZM17.7995 19.7994H6.17916C6.37472 20.1412 6.65692 20.4253 6.99728 20.6232C7.33763 20.8212 7.72414 20.9258 8.11786 20.9269H15.8829C16.2737 20.9261 16.6572 20.8212 16.994 20.6231C17.3309 20.4249 17.6089 20.1406 17.7995 19.7994Z"
							fill="currentColor"
						/>
					</svg>
				</div>
				<span class="text-xl font-bold tracking-tight">CoachRx</span>
			</div>
		</div>
		<div class="hidden md:flex items-center gap-8 text-[13px] font-medium text-gray-600">
			<a href="#" class="hover:text-black transition-colors">Features</a>
			<a href="#" class="hover:text-black transition-colors">Pricing</a>
			<a href="#" class="hover:text-black transition-colors">Resources</a>
			<a href="#" class="hover:text-black transition-colors">OPEX Education</a>
			<a href="#" class="bg-black text-white px-5 py-2 rounded text-[13px] font-medium hover:bg-gray-800 transition-colors">Start Free Trial</a>
		</div>
	</nav>

	<!-- Hero Section -->
	<section class="flex flex-col items-center pt-16 pb-20 px-4 text-center">
		<h1 class="text-4xl md:text-[56px] leading-[1.1] font-medium tracking-tight max-w-3xl mb-6">
			Build a sustainable<br>coaching business.
		</h1>
		<p class="text-gray-500 text-[15px] max-w-xl mb-8 leading-relaxed">
			The ultimate coaching software for fitness professionals. Design programs, track clients, and scale your practice with AI-assisted workflows—trusted by 8,000+ coaches worldwide.
		</p>
		<button class="bg-black text-white px-6 py-3 rounded text-[13px] font-medium hover:bg-gray-800 transition-colors mb-20">
			Start Free Trial
		</button>

		<!-- Horizontal Scroll Images -->
		<div class="w-full max-w-[1400px] overflow-hidden relative mt-12">
			<div class="flex gap-6 justify-center items-center h-[320px]">
				<!-- Image 1 -->
				<div class="w-[200px] h-[260px] rounded-[24px] overflow-hidden flex-shrink-0 relative group shadow-lg rotate-[-2deg] translate-y-4">
					<img src="/generated/image-fitness-coach-working-one-on-one-with-a--1767634090943-0.webp" alt="Coach working with client" class="w-full h-full object-cover" />
				</div>
				<!-- Image 2 -->
				<div class="w-[260px] h-[180px] rounded-[24px] overflow-hidden flex-shrink-0 relative group shadow-lg rotate-[1deg] -translate-y-2">
					<img src="/generated/image-personal-trainer-demonstrating-an-exerci-1767634094251-1.webp" alt="Trainer demonstrating exercise" class="w-full h-full object-cover" />
				</div>
				<!-- Image 3 -->
				<div class="w-[220px] h-[220px] rounded-[24px] overflow-hidden flex-shrink-0 relative group shadow-lg rotate-[-1deg] translate-y-2">
					<img src="/generated/image-fitness-coach-taking-notes-while-observi-1767634096990-2.webp" alt="Coach taking notes" class="w-full h-full object-cover" />
				</div>
				<!-- Image 4 -->
				<div class="w-[200px] h-[200px] rounded-[24px] overflow-hidden flex-shrink-0 relative group shadow-lg rotate-[2deg] -translate-y-4">
					<img src="/generated/image-coach-and-client-celebrating-progress-to-1767634099740-3.webp" alt="Celebrating progress" class="w-full h-full object-cover" />
				</div>
				<!-- Image 5 -->
				<div class="w-[180px] h-[260px] rounded-[24px] overflow-hidden flex-shrink-0 relative group shadow-lg rotate-[-2deg] translate-y-6">
					<img src="/generated/image-fitness-professional-working-at-desk-wit-1767634102587-4.webp" alt="Coach at desk" class="w-full h-full object-cover" />
				</div>
				<!-- Image 6 -->
				<div class="w-[200px] h-[160px] rounded-[24px] overflow-hidden flex-shrink-0 relative group shadow-lg rotate-[1deg] -translate-y-2">
					<img src="/generated/image-small-group-training-session-with-coach--1767634105551-5.webp" alt="Group training" class="w-full h-full object-cover" />
				</div>
			</div>
		</div>
	</section>

	<!-- App Showcase -->
	<section class="py-24 px-6 md:px-12 flex justify-center">
		<div class="bg-white rounded-[32px] p-12 md:p-20 flex flex-col md:flex-row items-center gap-16 max-w-[1200px] w-full shadow-sm">
			<!-- Phone Mockup -->
			<div class="relative w-[280px] h-[580px] bg-black rounded-[40px] p-3 shadow-2xl flex-shrink-0 border-4 border-gray-100">
				<div class="w-full h-full bg-white rounded-[32px] overflow-hidden relative">
					<!-- Fake App UI -->
					<div class="p-6 pt-10">
						<div class="flex justify-between items-center mb-6">
							<div class="text-xs font-bold">Good morning, Sarah</div>
							<div class="w-6 h-6 bg-gray-200 rounded-full"></div>
						</div>
						<div class="flex justify-between gap-2 mb-8">
							<div class="w-16 h-16 rounded-full border-4 border-red-400 flex items-center justify-center text-xs font-bold">25</div>
							<div class="w-16 h-16 rounded-full border-4 border-green-400 flex items-center justify-center text-xs font-bold">53</div>
							<div class="w-16 h-16 rounded-full border-4 border-blue-400 flex items-center justify-center text-xs font-bold">66</div>
						</div>
						<div class="bg-gray-50 p-4 rounded-xl mb-4">
							<div class="text-[10px] text-gray-500 uppercase mb-1">Biological Age</div>
							<div class="text-2xl font-bold">30 <span class="text-sm font-normal text-gray-500">years</span></div>
						</div>
						<div class="space-y-3">
							<div class="h-2 bg-gray-100 rounded full w-3/4"></div>
							<div class="h-2 bg-gray-100 rounded full w-1/2"></div>
							<div class="h-2 bg-gray-100 rounded full w-5/6"></div>
						</div>
					</div>
					<!-- Bottom Nav -->
					<div class="absolute bottom-0 left-0 w-full h-16 bg-white border-t border-gray-100 flex justify-around items-center px-4">
						<div class="w-6 h-6 bg-black rounded-full"></div>
						<div class="w-6 h-6 bg-gray-200 rounded-full"></div>
						<div class="w-6 h-6 bg-gray-200 rounded-full"></div>
						<div class="w-6 h-6 bg-gray-200 rounded-full"></div>
					</div>
				</div>
			</div>

			<!-- Content -->
			<div class="flex-1 max-w-lg">
				<h2 class="text-3xl font-medium mb-6 leading-tight">
					Everything in one place.<br>
					Design individualized programs with AI assistance.
					Track lifestyle, nutrition, and training.
					Manage your entire roster from a unified calendar.
					Scale to 40-60 high-value clients without burning out.
				</h2>
				<div class="flex items-center justify-between mt-12">
					<a href="#" class="flex items-center gap-2 text-blue-600 text-sm font-medium hover:underline">
						{@html PlayCircle}
						Watch demo
					</a>
					<div class="flex gap-4">
						<button class="w-8 h-8 flex items-center justify-center rounded-full border border-gray-200 hover:bg-gray-50 transition-colors">
							{@html ChevronLeft}
						</button>
						<button class="w-8 h-8 flex items-center justify-center rounded-full border border-gray-200 hover:bg-gray-50 transition-colors">
							{@html ChevronRight}
						</button>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- Lifestyle Grid -->
	<section class="py-20 px-6 md:px-12 max-w-[1400px] mx-auto w-full">
		<div class="flex flex-col md:flex-row justify-between items-start mb-16 gap-10">
			<h2 class="text-4xl md:text-5xl font-medium tracking-tight max-w-md leading-[1.1]">
				Coaching depth over volume. Career longevity over burnout.
			</h2>
			<p class="text-gray-500 text-[15px] max-w-md leading-relaxed">
				CoachRx empowers you to deliver truly individualized coaching at scale. Built for the OPEX Method but flexible for any coaching philosophy, our platform helps you maintain high-touch relationships while building a sustainable, profitable practice.
			</p>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
			<!-- Card 1 -->
			<div class="relative h-[480px] rounded-[32px] overflow-hidden group">
				<img src="/generated/image-confident-fitness-coach-standing-in-a-we-1767634108497-6.webp" alt="Professional coach" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
				<div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent flex flex-col justify-end p-8 text-white">
					<h3 class="text-2xl font-medium mb-2">Individual design made simple.</h3>
					<p class="text-sm text-white/80 leading-relaxed">Create personalized programs faster with RxBot AI assistance, templates, and a unified calendar for training, nutrition, and lifestyle.</p>
				</div>
			</div>
			<!-- Card 2 -->
			<div class="relative h-[480px] rounded-[32px] overflow-hidden group">
				<img src="/generated/image-coach-reviewing-client-progress-data-on--1767634111364-7.webp" alt="Coach reviewing data" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
				<div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent flex flex-col justify-end p-8 text-white">
					<h3 class="text-2xl font-medium mb-2">Data-driven coaching decisions.</h3>
					<p class="text-sm text-white/80 leading-relaxed">Track compliance, integrate wearables, monitor progress, and make informed adjustments with comprehensive analytics.</p>
				</div>
			</div>
			<!-- Card 3 -->
			<div class="relative h-[480px] rounded-[32px] overflow-hidden group">
				<img src="/generated/image-happy-client-giving-thumbs-up-to-their-c-1767634114176-8.webp" alt="Happy client" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
				<div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent flex flex-col justify-end p-8 text-white">
					<h3 class="text-2xl font-medium mb-2">Better client outcomes.</h3>
					<p class="text-sm text-white/80 leading-relaxed">Deliver consistent, high-quality coaching that keeps clients engaged and achieving results for the long term.</p>
				</div>
			</div>
		</div>
	</section>

	<!-- Testimonial -->
	<section class="py-24 px-6 text-center bg-[#F5F5F3]">
		<div class="max-w-3xl mx-auto">
			<blockquote class="text-2xl md:text-3xl font-medium leading-tight mb-10">
				"CoachRx transformed my coaching business. I went from drowning in spreadsheets and admin work to confidently managing 50+ clients with individualized programs. The AI assistance saves me hours every week, and my clients love the app experience."
			</blockquote>
			<div class="flex flex-col items-center gap-3">
				<img src="/generated/image-experienced-fitness-coach-in-their-30s-o-1767634116872-9.webp" alt="Coach testimonial" class="w-12 h-12 rounded-full object-cover" />
				<div class="text-sm">
					<div class="font-bold">Sarah Mitchell</div>
					<div class="text-gray-500">OPEX CCP Coach & Gym Owner</div>
				</div>
			</div>
		</div>
	</section>

	<!-- Process Steps -->
	<section class="py-20 px-6 md:px-12 max-w-[1400px] mx-auto w-full border-b border-gray-200">
		<div class="grid grid-cols-1 md:grid-cols-3 gap-12">
			<div>
				<h3 class="text-xl font-medium mb-2">Free migration support.</h3>
				<p class="text-sm text-gray-500 leading-relaxed">Dedicated transition team helps you move from Excel, TrueCoach, or any platform. One-on-one onboarding with practicing coaches.</p>
			</div>
			<div>
				<h3 class="text-xl font-medium mb-2">14-day full trial.</h3>
				<p class="text-sm text-gray-500 leading-relaxed">Test every feature with real clients. No credit card required. Experience the complete platform before committing.</p>
			</div>
			<div>
				<h3 class="text-xl font-medium mb-2">Transparent pricing.</h3>
				<p class="text-sm text-gray-500 leading-relaxed">Usage-based tiers by active client count. Scale as you grow. No hidden fees or surprise charges.</p>
			</div>
		</div>
	</section>

	<!-- How it works -->
	<section class="py-24 px-6 md:px-12 max-w-[1400px] mx-auto w-full">
		<div class="flex flex-col lg:flex-row gap-20">
			<!-- Sticky Title -->
			<div class="lg:w-1/3 lg:sticky lg:top-24 h-fit">
				<h2 class="text-4xl font-medium mb-6">How it works.</h2>
				<p class="text-gray-500 text-[15px] leading-relaxed max-w-xs">
					From sign-up to scaling your practice, CoachRx guides you through every step. Migrate your clients, design programs with AI assistance, and build a sustainable coaching business.
				</p>
			</div>

			<!-- Steps List -->
			<div class="lg:w-2/3 flex flex-col gap-8">
				<!-- Step 1 -->
				<div class="bg-white rounded-[32px] p-10 md:p-16 flex flex-col items-center text-center shadow-sm">
					<div class="w-full max-w-md mb-10 text-left self-start">
						<div class="w-8 h-8 rounded border border-gray-200 flex items-center justify-center text-xs font-medium mb-6">1</div>
						<h3 class="text-2xl font-medium mb-3">Start your free trial.</h3>
						<p class="text-sm text-gray-500 leading-relaxed">Sign up in minutes. No credit card required. Get 14 days of full access to test CoachRx with your real clients and workflows.</p>
					</div>
					<div class="w-[240px] h-[480px] bg-black rounded-[36px] p-2 shadow-xl border-4 border-gray-100">
						<div class="w-full h-full bg-white rounded-[28px] overflow-hidden relative flex flex-col">
                            <!-- Mock UI -->
                            <div class="bg-gray-50 p-4 border-b">
                                <div class="h-4 w-20 bg-gray-200 rounded mb-2"></div>
                            </div>
                            <div class="p-4 space-y-3">
                                <div class="h-12 bg-green-50 rounded-lg border border-green-100 p-2">
                                    <div class="h-2 w-12 bg-green-200 rounded mb-1"></div>
                                    <div class="h-4 w-24 bg-green-300 rounded"></div>
                                </div>
                                <div class="h-12 bg-white rounded-lg border border-gray-100 p-2">
                                    <div class="h-2 w-12 bg-gray-200 rounded mb-1"></div>
                                    <div class="h-4 w-24 bg-gray-300 rounded"></div>
                                </div>
                                <div class="h-12 bg-white rounded-lg border border-gray-100 p-2">
                                    <div class="h-2 w-12 bg-gray-200 rounded mb-1"></div>
                                    <div class="h-4 w-24 bg-gray-300 rounded"></div>
                                </div>
                            </div>
                        </div>
					</div>
				</div>

				<!-- Step 2 -->
				<div class="bg-white rounded-[32px] p-10 md:p-16 flex flex-col items-center text-center shadow-sm">
					<div class="w-full max-w-md mb-10 text-left self-start">
						<div class="w-8 h-8 rounded border border-gray-200 flex items-center justify-center text-xs font-medium mb-6">2</div>
						<h3 class="text-2xl font-medium mb-3">Migrate your clients.</h3>
						<p class="text-sm text-gray-500 leading-relaxed">Our dedicated transition team helps you move from Excel, Google Sheets, TrueCoach, or any platform. Free white-glove migration service included.</p>
					</div>
					<div class="w-[240px] h-[480px] bg-black rounded-[36px] p-2 shadow-xl border-4 border-gray-100">
                        <div class="w-full h-full bg-white rounded-[28px] overflow-hidden relative flex flex-col items-center pt-8">
                            <div class="text-sm font-bold mb-4">Import Clients</div>
                            <div class="w-16 h-16 bg-gray-100 rounded-full mb-4"></div>
                            <div class="text-xs text-gray-500 px-8 text-center">Seamlessly transfer all your client data and programs.</div>
                            <div class="mt-auto w-full p-4">
                                <div class="w-full h-10 bg-black rounded-lg"></div>
                            </div>
                        </div>
					</div>
				</div>

				<!-- Step 3 -->
				<div class="bg-white rounded-[32px] p-10 md:p-16 flex flex-col items-center text-center shadow-sm">
					<div class="w-full max-w-md mb-10 text-left self-start">
						<div class="w-8 h-8 rounded border border-gray-200 flex items-center justify-center text-xs font-medium mb-6">3</div>
						<h3 class="text-2xl font-medium mb-3">Design programs with AI.</h3>
						<p class="text-sm text-gray-500 leading-relaxed">Use RxBot to auto-generate and adjust training plans. Create individualized programs in minutes with templates, periodization tools, and unified calendar.</p>
					</div>
					<div class="w-[240px] h-[480px] bg-black rounded-[36px] p-2 shadow-xl border-4 border-gray-100">
                        <div class="w-full h-full bg-gray-900 rounded-[28px] overflow-hidden relative text-white p-6 pt-10">
                             <div class="flex items-center gap-3 mb-6">
                                 <div class="w-10 h-10 rounded-full bg-gray-700"></div>
                                 <div>
                                     <div class="text-sm font-bold">Client Program</div>
                                     <div class="text-[10px] text-gray-400">Week 4 - Strength</div>
                                 </div>
                             </div>
                             <div class="space-y-2">
                                 <div class="h-20 bg-gray-800 rounded-xl"></div>
                                 <div class="h-20 bg-gray-800 rounded-xl"></div>
                             </div>
                        </div>
					</div>
				</div>

				<!-- Step 4 -->
				<div class="bg-white rounded-[32px] p-10 md:p-16 flex flex-col items-center text-center shadow-sm">
					<div class="w-full max-w-md mb-10 text-left self-start">
						<div class="w-8 h-8 rounded border border-gray-200 flex items-center justify-center text-xs font-medium mb-6">4</div>
						<h3 class="text-2xl font-medium mb-3">Track and communicate.</h3>
						<p class="text-sm text-gray-500 leading-relaxed">Monitor client compliance, integrate wearables, send video/voice messages, and track progress across training, nutrition, and lifestyle in one place.</p>
					</div>
					<div class="w-[240px] h-[480px] bg-black rounded-[36px] p-2 shadow-xl border-4 border-gray-100">
                        <div class="w-full h-full bg-white rounded-[28px] overflow-hidden relative flex flex-col pt-8 px-4">
                            <div class="text-center text-sm font-bold mb-4">Client Progress</div>
                            <div class="text-[10px] text-gray-500 leading-relaxed text-justify">
                                Compliance: 92% this week
                                <br><br>
                                Training sessions completed: 4/4
                                <br><br>
                                Nutrition adherence: Excellent
                                <br><br>
                                Latest message: "Feeling strong on the new program!"
                            </div>
                        </div>
					</div>
				</div>

				<!-- Step 5 -->
				<div class="bg-white rounded-[32px] p-10 md:p-16 flex flex-col items-center text-center shadow-sm">
					<div class="w-full max-w-md mb-10 text-left self-start">
						<div class="w-8 h-8 rounded border border-gray-200 flex items-center justify-center text-xs font-medium mb-6">5</div>
						<h3 class="text-2xl font-medium mb-3">Scale your business.</h3>
						<p class="text-sm text-gray-500 leading-relaxed">Grow to 40-60 high-value clients without burning out. Manage billing via Stripe, create a storefront, and access business analytics to optimize your practice.</p>
					</div>
					<div class="w-[240px] h-[480px] bg-black rounded-[36px] p-2 shadow-xl border-4 border-gray-100">
                        <div class="w-full h-full bg-white rounded-[28px] overflow-hidden relative flex flex-col pt-8 px-4">
                             <div class="bg-gray-100 p-3 rounded-lg text-[10px] mb-2">
                                 Business Dashboard
                             </div>
                             <div class="text-[10px] text-gray-500 leading-relaxed mt-2">
                                 Active clients: 52
                                 <br><br>
                                 Monthly revenue: $6,240
                                 <br><br>
                                 Avg. client compliance: 88%
                                 <br><br>
                                 Client retention: 94%
                             </div>
                        </div>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- Dark Cards Section -->
	<section class="py-10 px-6 md:px-12 max-w-[1400px] mx-auto w-full">
		<div class="grid grid-cols-1 md:grid-cols-2 gap-6">
			<!-- Left Card -->
			<div class="bg-[#111] rounded-[32px] p-10 md:p-12 text-white min-h-[400px] flex flex-col relative overflow-hidden">
				<div class="relative z-10">
					<div class="text-xs text-gray-400 mb-2">Powered by OPEX Fitness.</div>
					<h3 class="text-2xl font-medium max-w-xs">Integrated with the OPEX education ecosystem and methodology.</h3>
				</div>
				<!-- Map Graphic Placeholder -->
				<div class="absolute bottom-0 right-0 w-full h-64 opacity-20">
                    <!-- Simple dot map simulation with SVG -->
                    <svg viewBox="0 0 200 100" class="w-full h-full">
                        {#each Array(100) as _, i}
                            <circle cx={Math.random() * 200} cy={Math.random() * 100} r="1" fill="white" />
                        {/each}
                    </svg>
				</div>
			</div>
			<!-- Right Card -->
			<div class="bg-[#111] rounded-[32px] p-10 md:p-12 text-white min-h-[400px] flex flex-col relative overflow-hidden">
				<div class="relative z-10">
					<div class="text-xs text-gray-400 mb-2">Seamless migration.</div>
					<h3 class="text-2xl font-medium max-w-xs">Free white-glove migration from any platform with dedicated support.</h3>
				</div>
				<!-- Blurred Text Graphic -->
				<div class="absolute bottom-8 right-8 text-right font-mono text-3xl opacity-30 blur-[2px] select-none pointer-events-none">
					<div>Excel|→CoachRx</div>
					<div>TrueCo|→CoachRx</div>
					<div>Sheets|→CoachRx</div>
					<div>Trainer|→CoachRx</div>
				</div>
			</div>
		</div>
	</section>

	<!-- Pricing Section -->
	<section class="py-24 px-6 md:px-12 max-w-[1400px] mx-auto w-full text-center">
		<h2 class="text-3xl md:text-4xl font-medium mb-4">Transparent, usage-based pricing.</h2>
		<p class="text-gray-500 text-sm max-w-lg mx-auto mb-16">
			Scale as you grow. Pay based on active client count. All plans include full platform access, AI assistance, migration support, and unlimited program design.
		</p>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-4xl mx-auto">
			<!-- Starter Plan -->
			<div class="bg-white rounded-[32px] p-8 text-left flex flex-col shadow-sm">
				<div class="w-10 h-10 bg-gray-100 rounded-lg mb-6"></div>
				<h3 class="text-xl font-bold mb-1">Starter</h3>
				<p class="text-xs text-gray-500 mb-6">Perfect for new coaches building their practice.</p>
				
				<div class="flex items-baseline gap-1 mb-1">
					<span class="text-2xl font-bold">$79</span>
					<span class="text-xs text-gray-500">/mo</span>
				</div>
				<div class="text-[10px] text-gray-400 mb-8">Up to 15 active clients</div>

				<ul class="space-y-4 mb-8 flex-1">
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Full platform access with AI-assisted program design
					</li>
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Unified calendar for training, nutrition, and lifestyle
					</li>
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Client mobile app, messaging, and compliance tracking
					</li>
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Free migration and onboarding support
					</li>
				</ul>

				<button class="w-full bg-black text-white py-3 rounded-lg text-xs font-bold hover:bg-gray-800 transition-colors">Start Free Trial</button>
			</div>

			<!-- Core Plan -->
			<div class="bg-white rounded-[32px] p-8 text-left flex flex-col shadow-sm border-2 border-orange-100 relative overflow-hidden">
                <div class="absolute top-0 right-0 bg-orange-100 text-orange-600 text-[10px] font-bold px-3 py-1 rounded-bl-xl">POPULAR</div>
				<div class="w-10 h-10 bg-orange-50 rounded-lg mb-6"></div>
				<h3 class="text-xl font-bold mb-1">Professional</h3>
				<p class="text-xs text-gray-500 mb-6">For established coaches scaling sustainably.</p>
				
				<div class="flex items-baseline gap-1 mb-1">
					<span class="text-2xl font-bold">$149</span>
					<span class="text-xs text-gray-500">/mo</span>
				</div>
				<div class="text-[10px] text-gray-400 mb-8">Up to 40 active clients</div>

				<ul class="space-y-4 mb-8 flex-1">
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Everything in Starter, plus advanced analytics
					</li>
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Wearable integrations and biometric tracking
					</li>
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Stripe billing integration and storefront creation
					</li>
					<li class="flex gap-3 text-xs text-gray-600">
						<span class="text-green-500 shrink-0">{@html Check}</span>
						Priority support and OPEX education discounts
					</li>
				</ul>

				<button class="w-full bg-black text-white py-3 rounded-lg text-xs font-bold hover:bg-gray-800 transition-colors">Start Free Trial</button>
			</div>
		</div>
		<p class="text-xs text-gray-500 mt-8">Need more than 40 clients? <a href="#" class="underline">Contact us</a> for Enterprise pricing.</p>
	</section>

	<!-- FAQ Section -->
	<section class="py-20 px-6 md:px-12 max-w-3xl mx-auto w-full">
		<h2 class="text-3xl font-medium text-center mb-16">Your questions answered.</h2>
		<div class="space-y-4">
			{#each faqs as faq, i}
				<button 
					class="w-full flex items-center justify-between p-4 text-left hover:bg-gray-100 rounded-lg transition-colors group"
					onclick={() => toggleFaq(i)}
				>
					<span class="text-sm font-medium text-gray-800">{faq.question}</span>
					<span class="text-gray-400 transition-transform duration-200 {faq.open ? 'rotate-45' : ''}">{@html Plus}</span>
				</button>
                {#if faq.open}
                    <div class="px-4 pb-4 text-xs text-gray-500">
                        {#if i === 0}
                            CoachRx provides a unified platform for program design, client management, and business operations. With AI-assisted workflows, you can design individualized programs faster, manage 40-60 clients without burnout, and maintain high-touch coaching relationships while scaling your revenue.
                        {:else if i === 1}
                            Yes! We offer free white-glove migration support. Our dedicated transition team helps you move from Excel, Google Sheets, TrueCoach, Trainerize, or any other platform. You'll get one-on-one onboarding with practicing coaches who understand your workflow.
                        {:else if i === 2}
                            CoachRx is built specifically for individual design coaching with AI assistance, unified calendar management, and deep OPEX integration. We focus on coaching depth over volume, helping you maintain sustainable practices with 40-60 high-value clients rather than pushing for hundreds of low-touch accounts.
                        {:else if i === 3}
                            No! While CoachRx is tightly integrated with OPEX's education ecosystem and optimized for the OPEX Method, it's flexible enough for any coaching philosophy. Coaches from all backgrounds use CoachRx to deliver individualized programming.
                        {:else if i === 4}
                            RxBot is our AI assistant that auto-generates and adjusts training plans based on your coaching methodology, client assessments, and program goals. It speeds up program design while maintaining your individual approach, saving hours of admin work each week.
                        {/if}
                    </div>
                {/if}
			{/each}
		</div>
		<div class="text-center mt-12">
			<button class="bg-white border border-gray-200 px-6 py-3 rounded text-xs font-medium hover:bg-gray-50 transition-colors">
				View all Frequently Asked Questions
			</button>
		</div>
	</section>

	<!-- Footer -->
	<footer class="bg-[#F5F5F3] py-16 px-6 md:px-12 text-[11px] text-gray-500">
		<div class="max-w-[1400px] mx-auto">
			<div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-12 gap-8">
				<div class="flex items-center gap-2">
					<div class="w-6 h-6 text-black">
						<svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path
								fill-rule="evenodd"
								clip-rule="evenodd"
								d="M5.0473 17.8386L5.69453 18.9586V18.9601H18.3003L18.9314 17.84H6.34063L6.82626 16.9993H19.4308L20.078 15.8807H7.47237L7.95715 15.0414H16.0358L16.0366 15.0429L16.0375 15.0414H20.5603L20.5612 15.0429L21.2084 13.9228L21.208 13.922L21.2084 13.9213H21.2075L14.9084 3.00677L14.9106 3.00296L14.9062 3.00296L13.6177 3.00296L5.0473 17.8386ZM14.261 4.12767L13.7751 4.96887L18.9438 13.9213H19.9139L14.261 4.12767ZM13.1286 6.08808L12.6467 6.9225L16.6749 13.9006L16.6634 13.9213H17.6511L13.1286 6.08808ZM11.9999 8.04225L8.60411 13.9213H15.3899L11.9999 8.04225ZM6.99833 3.30006C7.33866 3.10343 7.7248 2.99993 8.11786 3L2.30033 13.0776C2.10357 12.7371 2 12.3508 2 11.9575C2 11.5643 2.10357 11.178 2.30033 10.8375L6.17916 4.12006C6.37543 3.77951 6.65798 3.49669 6.99833 3.30006ZM9.08869 3H10.3816L3.43223 15.0384L2.785 13.9184L9.08869 3ZM11.3509 3H12.6424L4.56262 16.9963L3.91691 15.8777L11.3509 3ZM21.7064 13.0598C21.8988 12.7254 22 12.3463 22 11.9605C22 11.5746 21.8988 11.1956 21.7064 10.8611L17.8039 4.10233C17.6108 3.7681 17.3331 3.49057 16.9987 3.2976C16.6644 3.10463 16.2852 3.00302 15.8992 3.00296H15.8741L21.6931 13.082L21.7064 13.0598ZM17.7995 19.7994H6.17916C6.37472 20.1412 6.65692 20.4253 6.99728 20.6232C7.33763 20.8212 7.72414 20.9258 8.11786 20.9269H15.8829C16.2737 20.9261 16.6572 20.8212 16.994 20.6231C17.3309 20.4249 17.6089 20.1406 17.7995 19.7994Z"
								fill="currentColor"
							/>
						</svg>
					</div>
					<span class="text-lg font-bold tracking-tight text-black">CoachRx</span>
				</div>
				<div class="flex flex-wrap gap-6 font-medium text-gray-600">
					<a href="#" class="hover:text-black">Features</a>
					<a href="#" class="hover:text-black">Pricing</a>
					<a href="#" class="hover:text-black">Resources</a>
					<a href="#" class="hover:text-black">Terms & Conditions</a>
					<a href="#" class="hover:text-black">Privacy Policy</a>
				</div>
				<div class="flex gap-4">
					<a href="#" class="text-black hover:text-gray-600">{@html XIcon}</a>
					<a href="#" class="text-black hover:text-gray-600">{@html Instagram}</a>
					<a href="#" class="text-black hover:text-gray-600">{@html Linkedin}</a>
				</div>
			</div>
			
			<div class="space-y-4 leading-relaxed opacity-60">
				<p>CoachRx is a software platform operated by OPEX Fitness. The platform provides tools for fitness coaching, program design, and client management. CoachRx does not provide medical advice, diagnosis, or treatment. Coaches using the platform are independent professionals responsible for their own client relationships and services.</p>
				<p>Pricing is based on active client count and includes full platform access. Payment processing is handled through Stripe. Additional services such as OPEX education programs may require separate enrollment. For complete details, see our Terms & Conditions.</p>
				<p>By using CoachRx, you agree to our Terms of Service and Privacy Policy. © 2024 OPEX Fitness. All rights reserved.</p>
			</div>
		</div>
	</footer>
</div>

<style>
    /* Hide scrollbar for horizontal scroll */
    .overflow-hidden::-webkit-scrollbar {
        display: none;
    }
</style>

