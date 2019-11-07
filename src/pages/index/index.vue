<template>
	<view class="content">
		 <view class="usermotto">
			<notice-modal :closeFlag="closeFlag"></notice-modal>
		</view>
	</view>
</template>

<script>
	import NoticeModal from '@/components/noticeModal'
	export default {
		components: {
			NoticeModal
		},
		data() {
			return {
				closeFlag: false
			}
		},
		onLoad () {
			this.closeFlag = true
		},
		methods: {
		}
	}
</script>

<style>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 200px;
}
</style>
