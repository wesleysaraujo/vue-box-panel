<template>
	<div class="box-panel from-right is-visible">
		<header class="box-panel-header">
			<slot name="box-title-header"></slot>
			<a href="#" class="box-panel-close" v-on:click="$emit('close')"></a>
		</header>

		<div class="box-panel-container">
			<div class="box-panel-content">
				<slot name="box-content">

				</slot>
				<!-- your side content here -->
			</div> <!-- box-panel-content -->
		</div> <!-- box-panel-container -->
	</div> <!-- box-panel -->
</template>
<script>
	export default {
		name: 'boxPanel',
	}
</script>
<style>
	.box-panel {
		position: fixed;
		top: 0;
		left: 0;
		height: 100%;
		width: 90%;
		background: rgba(0, 0, 0, 0.6);
		-webkit-transition: width 2s;
		-moz-transition: width 2s;
		transition: width 2s;
	}
	.box-panel::after {
		/* overlay layer */
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: transparent;
		cursor: pointer;
		-webkit-transition: background 0.3s 0.3s;
		-moz-transition: background 0.3s 0.3s;
		transition: background 0.3s 0.3s;
	}
	.box-panel.is-visible {
		visibility: visible;
		-webkit-transition: visibility 2s 0s;
		-moz-transition: visibility 2s 0s;
		transition: visibility 2s 0s;
	}
	.box-panel.is-visible::after {
		background: rgba(0, 0, 0, 0.6);
		-webkit-transition: background 0.3s 0s;
		-moz-transition: background 0.3s 0s;
		transition: background 0.3s 0s;
	}
	.box-panel.is-visible .box-panel-close::before {

		-webkit-animation: box-close-1 0.6s 0.3s;
		-moz-animation: box-close-1 0.6s 0.3s;
		animation: box-close-1 0.6s 0.3s;
	}
	.box-panel.is-visible .box-panel-close::after {
		-webkit-animation: box-close-2 0.6s 0.3s;
		-moz-animation: box-close-2 0.6s 0.3s;
		animation: box-close-2 0.6s 0.3s;
	}

	@-webkit-keyframes box-close-1 {
		0%, 50% {
			-webkit-transform: rotate(0);
		}
		100% {
			-webkit-transform: rotate(45deg);
		}
	}
	@-moz-keyframes box-close-1 {
		0%, 50% {
			-moz-transform: rotate(0);
		}
		100% {
			-moz-transform: rotate(45deg);
		}
	}
	@keyframes box-close-1 {
		0%, 50% {
			-webkit-transform: rotate(0);
			-moz-transform: rotate(0);
			-ms-transform: rotate(0);
			-o-transform: rotate(0);
			transform: rotate(0);
		}
		100% {
			-webkit-transform: rotate(45deg);
			-moz-transform: rotate(45deg);
			-ms-transform: rotate(45deg);
			-o-transform: rotate(45deg);
			transform: rotate(45deg);
		}
	}
	@-webkit-keyframes box-close-2 {
		0%, 50% {
			-webkit-transform: rotate(0);
		}
		100% {
			-webkit-transform: rotate(-45deg);
		}
	}
	@-moz-keyframes box-close-2 {
		0%, 50% {
			-moz-transform: rotate(0);
		}
		100% {
			-moz-transform: rotate(-45deg);
		}
	}
	@keyframes box-close-2 {
		0%, 50% {
			-webkit-transform: rotate(0);
			-moz-transform: rotate(0);
			-ms-transform: rotate(0);
			-o-transform: rotate(0);
			transform: rotate(0);
		}
		100% {
			-webkit-transform: rotate(-45deg);
			-moz-transform: rotate(-45deg);
			-ms-transform: rotate(-45deg);
			-o-transform: rotate(-45deg);
			transform: rotate(-45deg);
		}
	}
	.box-panel-header {
		position: fixed;
		width: 90%;
		height: 50px;
		background: rgba(255, 255, 255, 0.96);
		z-index: 2;
		box-shadow: 0 1px 1px rgba(0, 0, 0, 0.08);
		-webkit-transition: top 0.3s 0s;
		-moz-transition: top 0.3s 0s;
		transition: top 0.3s 0s;
	}
	.box-panel-header h1 {
		font-weight: bold;
		color: #89ba2c;
		padding-left: 5%;
	}
	.from-right .box-panel-header, .from-left .box-panel-header {
		top: -50px;
	}
	.from-right .box-panel-header {
		right: 0;
	}
	.from-left .box-panel-header {
		left: 0;
	}
	.is-visible .box-panel-header {
		top: 0;
		-webkit-transition: top 0.3s 0.3s;
		-moz-transition: top 0.3s 0.3s;
		transition: top 0.3s 0.3s;
	}
	@media only screen and (min-width: 768px) {
		.box-panel-header {
			width: 95%;
		}
	}
	@media only screen and (min-width: 1170px) {
		.box-panel-header {
			width: 90%;
		}
	}

	.box-panel-close {
		position: absolute;
		top: 0;
		right: 0;
		height: 100%;
		width: 60px;
    	border: none;
		/* image replacement */
		display: inline-block;
		overflow: hidden;
		text-indent: 100%;
		
	}
	.box-panel-close::before, .box-panel-close::after {
		/* close icon created in CSS */
		position: absolute;
		top: 22px;
		left: 20px;
		height: 3px;
		width: 20px;
		background-color: #424f5c;
		/* this fixes a bug where pseudo elements are slighty off position */
		-webkit-backface-visibility: hidden;
		backface-visibility: hidden;
		content: "\00d7";
	}
	.box-panel-close::before {
		-webkit-transform: rotate(45deg);
		-moz-transform: rotate(45deg);
		-ms-transform: rotate(45deg);
		-o-transform: rotate(45deg);
		transform: rotate(45deg);
		
	}
	.box-panel-close::after {
		-webkit-transform: rotate(-45deg);
		-moz-transform: rotate(-45deg);
		-ms-transform: rotate(-45deg);
		-o-transform: rotate(-45deg);
		transform: rotate(-45deg);
	}
	.no-touch .box-panel-close:hover {
		background-color: #424f5c;
	}
	.no-touch .box-panel-close:hover::before, .no-touch .box-panel-close:hover::after {
		background-color: #ffffff;
		-webkit-transition-property: -webkit-transform;
		-moz-transition-property: -moz-transform;
		transition-property: transform;
		-webkit-transition-duration: 0.3s;
		-moz-transition-duration: 0.3s;
		transition-duration: 0.3s;
	}
	.no-touch .box-panel-close:hover::before {
		-webkit-transform: rotate(220deg);
		-moz-transform: rotate(220deg);
		-ms-transform: rotate(220deg);
		-o-transform: rotate(220deg);
		transform: rotate(220deg);
	}
	.no-touch .box-panel-close:hover::after {
		-webkit-transform: rotate(135deg);
		-moz-transform: rotate(135deg);
		-ms-transform: rotate(135deg);
		-o-transform: rotate(135deg);
		transform: rotate(135deg);
	}

	.box-panel-container {
		position: fixed;
		width: 90%;
		height: 100%;
		top: 0;
		background: #fefefe;
		z-index: 1;
		-webkit-transition-property: -webkit-transform;
		-moz-transition-property: -moz-transform;
		transition-property: transform;
		-webkit-transition-duration: 0.3s;
		-moz-transition-duration: 0.3s;
		transition-duration: 0.3s;
		-webkit-transition-delay: 0.3s;
		-moz-transition-delay: 0.3s;
		transition-delay: 0.3s;
	}
	.from-right .box-panel-container {
		right: 0;
		-webkit-transform: translate3d(100%, 0, 0);
		-moz-transform: translate3d(100%, 0, 0);
		-ms-transform: translate3d(100%, 0, 0);
		-o-transform: translate3d(100%, 0, 0);
		transform: translate3d(100%, 0, 0);
	}
	.from-left .box-panel-container {
		left: 0;
		-webkit-transform: translate3d(-100%, 0, 0);
		-moz-transform: translate3d(-100%, 0, 0);
		-ms-transform: translate3d(-100%, 0, 0);
		-o-transform: translate3d(-100%, 0, 0);
		transform: translate3d(-100%, 0, 0);
	}
	.is-visible .box-panel-container {
		-webkit-transform: translate3d(0, 0, 0);
		-moz-transform: translate3d(0, 0, 0);
		-ms-transform: translate3d(0, 0, 0);
		-o-transform: translate3d(0, 0, 0);
		transform: translate3d(0, 0, 0);
		-webkit-transition-delay: 0s;
		-moz-transition-delay: 0s;
		transition-delay: 0s;
	}
	@media only screen and (min-width: 768px) {
		.box-panel-container {
			width: 95%;
		}
	}
	@media only screen and (min-width: 1170px) {
		.box-panel-container {
			width: 90%;
		}
	}

	.box-panel-content {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		padding: 5% 3%;
		overflow: auto;
		/* smooth scrolling on touch devices */
		-webkit-overflow-scrolling: touch;
		box-sizing: border-box;
		text-align: left;
	}
	.box-panel-content p {
		font-size: 14px;
		font-size: 0.875rem;
		color: #424f5c;
		line-height: 1.4;
		margin: 2em 0;
	}
	.box-panel-content p:first-of-type {
		margin-top: 0;
	}
	@media only screen and (min-width: 768px) {
		.box-panel-content p {
			font-size: 16px;
			font-size: 1rem;
			line-height: 1.6;
		}
	}

</style>