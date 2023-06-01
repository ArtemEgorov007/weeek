<template>
	<header class="header">
		<div class="header__container">
			<div class="header__logotip">
				<img class="header__logotip-images" src="@/assets/svg/logotip.svg" alt="Логотип" />
			</div>

			<div class="header__right">
				<div class="header__right-wrapper">
					<div class="header__buttons">
						<button class="header__button">Login</button>
					</div>
					<div class="header__languages">
						<select class="header__language-select">
							<option class="header__language-option" value="en">🇺🇸&emsp;EN</option>
							<option class="header__language-option" value="ru">🇷🇺&emsp;RU</option>
						</select>
					</div>
					<div class="header__languages">
						<div class="header__language" @click="toggleDropdown">
							<img src="@/assets/svg/English.svg" alt="English" />
							<span class="header__language-text">{{ currentLanguage }}</span>
							<ul v-if="isDropdownOpen" class="language-dropdown">
								<li v-for="language in languages" :key="language.code" @click="selectLanguage(language)">
									<img :src="language.icon" :alt="language.name" />
									<span>{{ language.code }}</span>
								</li>
							</ul>
						</div>
					</div>
				</div>
			</div>
		</div>
	</header>
</template>

<script>
export default {
	data() {
		return {
			isDropdownOpen: false,
			currentLanguage: "EN",
			languages: [
				{ code: "EN", name: "English", icon: "@/assets/svg/English.svg" },
				{ code: "RU", name: "Russian", icon: "@/assets/svg/English.svg" }
				// Add more languages as needed
			]
		};
	},
	methods: {
		toggleDropdown() {
			this.isDropdownOpen = !this.isDropdownOpen;
		},
		selectLanguage(language) {
			this.currentLanguage = language.code;
			this.isDropdownOpen = false;
			// Perform any other actions when language is selected
		}
	}
};
</script>

<style lang="scss">
.header {
	background: linear-gradient(225deg, rgba(255, 255, 255, 0.46) 0.78%, rgba(255, 255, 255, 0) 100%) #6788f3;
	height: 82px;

	&__container {
		display: flex;
		justify-content: space-around;
		align-items: center;
		height: 100%;
		margin: 0 auto;
		max-width: 1200px;
		padding: 0 20px;
	}

	&__logotip-images {
		cursor: pointer;
	}

	&__button {
		padding: 10px 32px 10px 32px;
		color: #fff;
		border: none;
		cursor: pointer;
		font-size: 16px;
	}

	&__buttons {
		width: 106px;
		height: 44px;
		background-color: #6788f3;
		border-radius: 8px;
	}

	&__languages {
		display: flex;
		align-items: center;
	}

	&__logotip img {
		width: 275px;
		height: 32px;
	}

	&__right-wrapper {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 0 36px;
	}

	&__languages {
		position: relative;
		background: #e3e4e8;
		width: 64px;
		height: 32px;
		border-radius: 8px;
	}

	&__language-select {
		display: flex;
		align-items: center;
		width: 60px;
		height: 28px;
		appearance: none;
		background: #ffffff;
		box-shadow: 0px 3px 8px rgba(0, 0, 0, 0.1), 0px 1px 1px rgba(0, 0, 0, 0.01), 0px 3px 1px rgba(0, 0, 0, 0.03);
		border-radius: 6px;
		border: none;
		text-align: end;
		margin: 2px;
		outline: none;
		padding: 5px;
		cursor: pointer;
		font-size: 14px;
		font-weight: 700;
		color: #7b8193;
	}

	&__language-option {
		padding: 15px;
		flex-wrap: wrap;
		cursor: pointer;
	}

	&__language-images {
		width: 16px;
		height: 16px;
	}

	custom-select {
		position: relative;
		display: inline-block;
	}

	.select-trigger {
		padding: 8px;
		border: 1px solid #ccc;
		background-color: #fff;
		cursor: pointer;
	}

	.dropdown-list {
		position: absolute;
		top: 100%;
		left: 0;
		width: 100%;
		max-height: 200px;
		overflow-y: auto;
		background-color: #fff;
		border: 1px solid #ccc;
		z-index: 999;
		display: none;
	}

	.dropdown-item {
		padding: 8px;
		cursor: pointer;
	}

	.dropdown-item:hover {
		background-color: #f9f9f9;
	}

	.custom-select.active .dropdown-list {
		display: block;
	}
}
</style>
