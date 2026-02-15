<script lang="ts">
	import { base } from '$app/paths';
	import { onMount } from 'svelte';

	interface Feature {
		title: string;
		description: string;
		details: string[];
		icon?: string;
	}

	interface App {
		name: string;
		description: string;
		subtitle: string;
		features: Feature[];
		tech: string[];
		github?: string;
		icon: string;
		details: string;
	}

	const apps: App[] = [
		{
			name: 'S3rp3nt Media',
			subtitle: 'Universal Media Viewer',
			description: 'A modern, feature-rich media viewer built with Qt 6, designed to provide a beautiful and immersive experience for viewing images, videos, audio files, documents, and more.',
			details: 'Experience media like never before with dynamic color extraction, real-time visualizations, and GPU-accelerated effects. S3rp3nt Media adapts to your content, creating an immersive viewing experience that matches the mood and colors of your media.',
			features: [
				{
					title: 'Universal Media Support',
					description: 'View any media format with ease',
					icon: 'images',
					details: [
						'Images: PNG, JPG, JPEG, BMP, GIF, WebP with animated GIF support',
						'Videos: MP4, AVI, MOV, MKV, WebM, M4V, FLV, WMV, MPG, MPEG, 3GP',
						'Audio: MP3, WAV, FLAC, OGG, AAC, M4A, WMA, Opus, MP2, MP1, AMR',
						'Documents: PDF viewer, text files with syntax highlighting, Markdown rendering, code files with language-specific highlighting'
					]
				},
				{
					title: 'Advanced Audio Features',
					description: 'Professional audio experience',
					icon: 'music',
					details: [
						'Real-time audio visualizer with frequency spectrum analysis',
						'FFT-based frequency band visualization with bass amplitude detection',
						'10-band equalizer (Beta) with custom audio processor',
						'Automatic lyrics fetching from LRC Lib with synchronized display',
						'Lyrics translation support via RapidAPI',
						'WASAPI loopback audio capture for system-wide visualization'
					]
				},
				{
					title: 'Dynamic Visual Effects',
					description: 'Beautiful, adaptive interface',
					icon: 'palette',
					details: [
						'Automatic dominant color extraction from media',
						'Spotify-style multi-color gradient backgrounds',
						'Apple Music-style blurred and darkened backdrops',
						'GPU-accelerated animated ambient gradients',
						'Procedural shader-based snow effect with 3D rotation',
						'Interface colors adapt to match current media'
					]
				},
				{
					title: 'User Experience',
					description: 'Designed for productivity',
					icon: 'sliders-h',
					details: [
						'Drag & drop file support',
						'Keyboard shortcuts (Ctrl+O to open)',
						'System tray integration',
						'Single instance management',
						'Custom title bar with window controls',
						'Multi-language support (English, Romanian)',
						'Comprehensive metadata display'
					]
				}
			],
			tech: ['Qt 6', 'QML', 'C++', 'OpenGL', 'WASAPI', 'FFmpeg'],
			github: 'https://github.com/MotanOfficial/s3rp3nt_media',
			icon: 'film'
		},
		{
			name: 'S3rp3nt Vision',
			subtitle: 'Windows Shell Extension',
			description: 'A Windows Shell Extension that provides PDF, WebP, and WebM thumbnails in Windows Explorer using PDFium, libwebp, and libvpx.',
			details: 'Enhance your Windows Explorer experience with beautiful thumbnails for PDF, WebP, and WebM files. S3rp3nt Vision integrates seamlessly into Windows, providing instant visual previews of your files directly in Explorer.',
			features: [
				{
					title: 'Thumbnail Generation',
					description: 'See your files at a glance',
					icon: 'image',
					details: [
						'PDF thumbnail generation using PDFium library',
						'WebP image thumbnail support with libwebp',
						'WebM video thumbnail support with libvpx',
						'Proper aspect ratio and scaling',
						'Automatic file type detection',
						'High-quality rendering'
					]
				},
				{
					title: 'Windows Integration',
					description: 'Seamless system integration',
					icon: 'windows',
					details: [
						'COM-based architecture for Windows integration',
						'Implements Windows IThumbnailProvider interface',
						'Runs in separate process (dllhost.exe) for security',
						'Easy installation via regsvr32',
						'Qt Installer Framework integration support',
						'Automatic registration during installation'
					]
				},
				{
					title: 'Performance & Safety',
					description: 'Optimized and secure',
					icon: 'shield-alt',
					details: [
						'PDF size limit to 100MB for safety',
						'Proper PDFium initialization and cleanup',
						'Efficient memory management',
						'Fast thumbnail generation',
						'Thread-safe implementation',
						'Error handling and recovery'
					]
				}
			],
			tech: ['C++', 'Windows COM', 'PDFium', 'libwebp', 'libvpx', 'CMake'],
			github: 'https://github.com/MotanOfficial/S3rp3nt_Vision',
			icon: 'eye'
		}
	];

	let mounted = false;
	let showScrollTop = false;

	onMount(() => {
		mounted = true;
		
		// Show/hide scroll to top button
		const handleScroll = () => {
			showScrollTop = window.scrollY > 300;
		};
		
		window.addEventListener('scroll', handleScroll);
		
		// Scroll-triggered animations for sections
		const observerOptions = {
			threshold: 0.1,
			rootMargin: '0px 0px -50px 0px'
		};
		
		const observer = new IntersectionObserver((entries) => {
			entries.forEach(entry => {
				if (entry.isIntersecting) {
					entry.target.classList.add('in-view');
				}
			});
		}, observerOptions);
		
		// Observe all feature sections
		document.querySelectorAll('.feature-section, .app-description-section, .tech-section-full, .download-section').forEach(el => {
			observer.observe(el);
		});
		
		return () => {
			window.removeEventListener('scroll', handleScroll);
			observer.disconnect();
		};
	});

	function scrollToTop() {
		window.scrollTo({ top: 0, behavior: 'smooth' });
	}
</script>

<svelte:head>
	<title>S3rp3nt - Modern App Suite</title>
	<meta name="description" content="S3rp3nt - A collection of modern, feature-rich applications for media viewing and Windows integration." />
	<style>
		@import url('https://fonts.googleapis.com/css2?family=Bowlby+One+SC&family=Outfit:wght@100..900&display=swap');
	</style>
</svelte:head>

<div class="page-wrapper">
	<!-- Animated Background -->
	<div class="animated-bg"></div>
	
	<!-- Modern Background Elements -->
	<div class="bg-orb bg-orb-1"></div>
	<div class="bg-orb bg-orb-2"></div>
	<div class="bg-orb bg-orb-3"></div>
	<div class="bg-orb bg-orb-4"></div>
	
	<div class="bg-grid"></div>
	<div class="bg-glow bg-glow-1"></div>
	<div class="bg-glow bg-glow-2"></div>
	
	<div class="container">
		<!-- Hero Section -->
		<section class="hero" class:visible={mounted}>
			<div class="hero-content">
				<div class="hero-title-wrapper">
					<h1 class="hero-title">
						<span class="gradient-text">S3rp3nt</span>
					</h1>
					<img
						src={`${base}/logo.png`}
						alt="S3rp3nt Logo"
						class="hero-logo"
					/>
				</div>
				<h2 class="hero-subtitle">
					A <em>modern</em> but complete
					<strong>app suite</strong>
					<strong>for Windows</strong>
				</h2>
				<p class="hero-description">
					Professional applications designed for media viewing and Windows integration.
					Built with modern technologies and attention to detail.
				</p>
				<div class="hero-buttons">
					<a href="https://github.com/MotanOfficial/s3rp3nt_media" target="_blank" rel="noopener noreferrer" class="hero-button hero-button-primary">
						<i class="fas fa-film"></i>
						Try S3rp3nt Media
					</a>
					<a href="https://github.com/MotanOfficial/S3rp3nt_Vision" target="_blank" rel="noopener noreferrer" class="hero-button hero-button-secondary">
						<i class="fas fa-eye"></i>
						Try S3rp3nt Vision
					</a>
				</div>
			</div>
		</section>

		<!-- Apps Section -->
		<section class="apps-section">
			{#each apps as app, appIndex}
				<article class="app-page" class:visible={mounted} style="animation-delay: {appIndex * 0.2}s">
					<!-- App Header -->
					<div class="app-hero">
						<div class="app-icon-large">
							{#if app.icon === 'film'}
								<i class="fas fa-film"></i>
							{:else if app.icon === 'eye'}
								<i class="fas fa-eye"></i>
							{/if}
						</div>
						<div class="app-title-section">
							<h2 class="app-name-large">{app.name}</h2>
							<p class="app-subtitle">{app.subtitle}</p>
						</div>
					</div>

					<!-- Main Content - Alternating Layout -->
					<div class="app-content">
						<!-- Description Section -->
						<section class="app-description-section">
							<div class="description-content">
								<h3 class="section-heading">An Intuitive Experience</h3>
								<aside class="description-text">
									<p>{app.description}</p>
									<p>{app.details}</p>
								</aside>
							</div>
						</section>

						<!-- Features Sections -->
						{#each app.features as feature, featureIndex}
							<section class="feature-section" class:reverse={featureIndex % 2 === 1}>
								<div class="feature-visual">
									<div class="feature-icon-wrapper">
										{#if feature.icon === 'images'}
											<i class="fas fa-images"></i>
										{:else if feature.icon === 'music'}
											<i class="fas fa-music"></i>
										{:else if feature.icon === 'palette'}
											<i class="fas fa-palette"></i>
										{:else if feature.icon === 'sliders-h'}
											<i class="fas fa-sliders-h"></i>
										{:else if feature.icon === 'image'}
											<i class="fas fa-image"></i>
										{:else if feature.icon === 'windows'}
											<i class="fab fa-windows"></i>
										{:else if feature.icon === 'shield-alt'}
											<i class="fas fa-shield-alt"></i>
										{/if}
									</div>
								</div>
								<div class="feature-content">
									<h3 class="feature-title">{feature.title}</h3>
									<p class="feature-description">{feature.description}</p>
									<ul class="feature-list">
										{#each feature.details as detail}
											<li>{detail}</li>
										{/each}
									</ul>
								</div>
							</section>
						{/each}

						<!-- Technologies Section -->
						<section class="tech-section-full">
							<h3 class="section-heading">Technologies</h3>
							<div class="tech-tags">
								{#each app.tech as tech}
									<span class="tech-tag">{tech}</span>
								{/each}
							</div>
						</section>

						<!-- CTA Section -->
						{#if app.github}
							<section class="download-section">
								<div class="download-content">
									<h3 class="section-heading">Ready to try it?</h3>
									<p class="download-text">
										S3rp3nt {app.name.split(' ')[1]} is free and open source.
										Feel free to give it a try!
									</p>
									<a href={app.github} target="_blank" rel="noopener noreferrer" class="github-link">
										<i class="fab fa-github"></i>
										View on GitHub
									</a>
								</div>
							</section>
						{/if}
					</div>
				</article>
			{/each}
		</section>
	</div>

	<!-- Footer -->
	<footer class="footer">
		<p>Made with ❤️ by MotanOfficial</p>
		<p class="footer-links">
			<a href="https://github.com/MotanOfficial" target="_blank" rel="noopener noreferrer">
				<i class="fab fa-github"></i> GitHub
			</a>
		</p>
	</footer>

	<!-- Scroll to Top Button -->
	<button 
		class="scroll-to-top" 
		class:visible={showScrollTop}
		on:click={scrollToTop}
		aria-label="Scroll to top"
	>
		<i class="fas fa-arrow-up"></i>
	</button>
</div>
