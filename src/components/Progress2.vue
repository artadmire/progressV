<template>
  <div class="my-progress">
		<button @click="changePlay">{{isPlay ? '暂停' : '播放'}}</button>
		<button @click="replay">重播</button>
		<div class="g-contain">
			<div 
			:class="['g-progress', isPlay ? 'animationplay': 'animationpause', type ? 'replay' : 'play'  ]" 
			@animationEnd="end"
			>
			</div>
		</div>
		
  </div>
   
</template>

<script>
import List from './List.vue'
export default {
  name: "Progress",
	components: {
    List
  },
	data() {
		return {
			isPlay: false,
			type: 0, // 0播放, 1 重播
			totalTime: 2,
		}
	},
	methods: {
		end(){},

		changePlay() {
			const { isPlay } = this;
			this.isPlay = !isPlay;
		},
		replay() {
			const { type } = this;
			this.isPlay = true;
			this.type = type ? 0 : 1;
		}
	}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	@keyframes play { 
    0% {  
      transform: translateX(-50%) scaleX(0);  /* 用 scaleX 来代替 width */
    }
		to {
					transform: translateX(0) scaleX(1);
		}
	}

	@keyframes replay {
    0% {  
      transform: translateX(-50%) scaleX(0);  /* 用 scaleX 来代替 width */
    }
		to {
					transform: translateX(0) scaleX(1);
		} 
	}
	.g-contain {
		width: 240px;
		height: 25px;
		border-radius: 25px;
		background: #eee;
		overflow: hidden;
}
	.g-progress {
		width: 100%;
		height: inherit;
		border-radius: 25px 0 0 25px;
		background: #0f0;
		will-change: transform; /**通知浏览器提前过好优化 */ 
		animation-timing-function: linear;
		-webkit-animation-timing-function: linear;
	}
	.g-progress.play {
		animation: play 3s infinite linear;
	}
	.g-progress.replay {
		animation: replay 3s infinite linear;
	}
	.g-progress.animationplay {     /* 使animation动画启动 */
		animation-play-state: running;
    -webkit-animation-play-state: running;
	}

	.g-progress.animationpause {    /* 使animation动画暂停 */
		animation-play-state: paused;
		-webkit-animation-play-state: paused;
	}
</style>

