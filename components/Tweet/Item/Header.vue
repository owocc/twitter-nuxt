<template>
	<div class="p-4 flex">
		<div>
			<img :src="author.profileImage" alt="" class="w-10 h-10 rounded-full" />
		</div>
		<div class="ml-3">
			<span class="font-medium text-gray-800 dark:text-white">{{ author.name }}</span>
			<span class="ml-3 text-sm font-medium text-gray-400">
				<nuxt-link to="#">
					{{ author.handle }}
				</nuxt-link>
				发布于 {{ props.tweet.postedAtHuman }}
			</span>
			<p v-if="props.tweet.replyTo" class="text-sm">
				<span class="text-gray-500">
					回复
				</span>
				<nuxt-link class="text-blue-400" :to='replyToTweeUrl'>{{ props.tweet.replyTo.author.handle }}</nuxt-link>
			</p>
		</div>
	</div>
</template>

<script setup lang=ts>
interface Props {
	tweet: any
}
const props = defineProps<Props>()
const author = props.tweet.author
const replyToTweeUrl = computed(() => `/status/${props.tweet?.replyTo?.id}`)
</script>