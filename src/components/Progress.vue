<template>
  <div class="my-progress">
		<button @click="changePlay">{{isPlay ? '暂停' : '播放'}}</button>
		<button @click="replay">重播</button>
		<div class="g-contain">
			<p class="g-progress" :style="{width: progress + '%'}"></p>
		</div>
		<List></List>
  </div>
   
</template>

<script>
import List from './List.vue'
let timer, totalTime = 3000;
export default {
  name: "Progress",
	components: {
    List
  },
	data() {
		return {
			isPlay: false,
			progress: 0,
			arr: []
		}
	},
	created() {
		for(let i = 0; i < 100000; i ++) {
			this.arr[i] = i;
		}
	},
	
	methods: {
		run() {
			timer = setInterval(() => {
				const {progress} = this;
				this.progress = progress + 1;
				if(this.progress === 100) {
					this.cancel();
				}
			}, totalTime / 100)
		},
		cancel() {
			clearInterval(timer);
			timer = null;
		},
		changePlay() {
			const { isPlay } = this;
			this.isPlay = !isPlay;
			if(this.isPlay) {
				this.run();
			} else {
				this.cancel();
			}
		},
		replay() {
			this.isPlay = true;
			this.progress = 0;
			this.run();
		}
	}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.g-contain {
		width: 240px;
		height: 25px;
		border-radius: 25px;
		background: #eee;
		overflow: hidden;
}
	.g-progress {
		height: inherit;
		border-radius: 25px 0 0 25px;
		background: #0f0;
	}
</style>
