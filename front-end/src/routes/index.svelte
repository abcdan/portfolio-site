<script>
	import Img from "../components/common/StandardImage.svelte"
	import AboutMeManager from "../components/about-me-tags/AboutMeManager.svelte"
	import ContactManager from "../components/contact/ContactManager.svelte"
	import ProjectManager from "../components/projects/ProjectManager.svelte"
	import Container from "../components/common/Container.svelte";
	import Card from "../components/common/Card.svelte";

	function calculateAge(birthday) { // birthday is a date
		let ageDifMs = Date.now() - birthday;
		let ageDate = new Date(ageDifMs); // miliseconds from epoch
		return Math.abs(ageDate.getUTCFullYear() - 1970);
	}

	// So the age is always up to date
	const age = calculateAge(new Date(2000, 12, 22));
</script>

<style>
	section {
		text-align: center;
	}

	.spacing {
		padding: 2%;
		display: flex;
        justify-content: center;
        align-items: center;
	}

	.header-height {
		min-height: 54vh;
		margin-right: 2.5%;
		width: 100%;
		padding: 20px;
	}

	.projects {
		display: block;
		width: 100%;
	}

	p, h2 {
		padding: 1%;
	}

	.contacts {
		margin-left: 2.5%;
		display: inline-block;
		width: 27.5%;
		float: left;
	}

	.about-me {
		display: inline-block;
		width: 70%;
	}

	.icon {
		width: 60%;
	}

	.header {
		padding: 20px;
	}

	@media (max-width: 1000px) {
		.icon {
			display: none;
		}

		.contact-manager {
			width: 40%;
			margin: 0 auto;
		}

		.contacts {
			position: relative;
			display: block;
			width: 100%;
			margin-bottom: 25px;
		}

		.about-me {
			width: 100%;
			
		}

		.header-height {
			height: auto;
		}

		.projects {
			display: block;
			position: relative;
			width: 100%;
			float: none;
			margin: 0;
		}
	}
	@media (max-width: 450px) {
		.contact-manager {
			width: 50%;
			margin: 0 auto;
		}
	}
</style>

<svelte:head>
	<title>Lukas portfolio</title>
	<meta name="title" content="Lukas portfolio">
	<meta name="description" content="Lukas van den Berk a developer his portfolio site">
	<meta property="og:type" content="website">
	<meta property="og:url" content="https://lukas.sh">
	<meta property="og:title" content="Lukas portfolio">
	<meta property="og:description" content="Lukas van den Berk a developer his portfolio site">
	<meta property="og:image" content="/favicon.png">
	<meta property="twitter:card" content="summary_large_image">
	<meta property="twitter:url" content="https://lukas.sh">
	<meta property="twitter:title" content="Lukas portfolio">
	<meta property="twitter:description" content="Lukas van den Berk a developer his portfolio site">
	<meta property="twitter:image" content="/favicon.png">
</svelte:head>

<Container>
	<section class="header-height header">
		<Card>
			<div class="header-height">
				<div class="contacts">
					<div class="icon">
						<Img src="favicon.png" alt="my-head" />
					</div>
					<div class="contact-manager">
						<ContactManager />
					</div>
				</div>
				<div class="about-me">
					<h2><b>Hello, I am Lukas van den Berk</b></h2>
					<h2>And I am a:</h2>
					<div class="spacing">
						<AboutMeManager />
					</div>
					<h2>About me</h2>
					<p>
						Hi there my name is Lukas van den Berk a {age} year old software engineer from the Netherlands.
						I am currently following an eduction in Software Development at Hogeschool Leiden (will be done in 2023).
						Below you will find some projects that I have done (in my freetime) to give you an idea of what I am capable of and what my interests are.
						<br>
						For exact skills check my LinkedIn in on the left.
					</p>
					<p>
						The source code of this project is available on <a href="https://github.com/lukasvdberk/portfolio-site">github</a>
					</p>
				</div>
			</div>
		</Card>
	</section>
	<section class="projects">
		<h2>Projects</h2>
		<ProjectManager />
	</section>
</Container>

