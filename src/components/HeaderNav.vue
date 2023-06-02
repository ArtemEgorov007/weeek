<template>
	<header class="header">
		<div class="header__container">

			<div class="header__logotip">
				<img class="header__logotip-images" src="@/assets/svg/logotip.svg" alt="Логотип" />
			</div>

			<div class="header__right">
				<div class="header__right-wrapper">
					<div class="header__buttons">
						<button class="header__button-size">{{ $t("button") }}</button>
					</div>

					<div class="header__languages">
						<div class="header__language-select" @click="toggleDropdown">
							<img class="header__language-images" src="@/assets/svg/English.svg" alt="English" />
							<span class="header__language-option">EN</span>
						</div>
					</div>


				</div>
			</div>
		</div>
	</header>
</template>

<script setup>
import { useI18n } from "vue-i18n";

const { locale } = useI18n({
	useScope: "global"
});

const toggleDropdown = () => (locale.value === "en" ? (locale.value = "ru") : (locale.value = "en"));
</script>

<style lang="scss">
.header {
	background: linear-gradient(225deg, rgba(255, 255, 255, 0.46) 0.78%, rgba(255, 255, 255, 0) 100%) #6788f3;
	height: 82px;

	&__container {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 100%;
		margin: 0 auto;
		max-width: 1240px;
		padding: 0 20px;
	}

	&__logotip-images {
		cursor: pointer;
	}

	&__button-size {
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
		background: #ffffff;
		box-shadow: 0px 3px 8px rgba(0, 0, 0, 0.1), 0px 1px 1px rgba(0, 0, 0, 0.01), 0px 3px 1px rgba(0, 0, 0, 0.03);
		border-radius: 6px;
		text-align: end;
		margin: 2px;
		padding: 5px;
		cursor: pointer;
		font-size: 14px;
		font-weight: 700;
		color: #7b8193;
	}

	&__language-option {
		padding: 15px;
		cursor: pointer;
	}

	&__language-images {
		width: 16px;
		height: 16px;
	}
}
</style>
