<template>
	<header class="absolute top-0 left-0 right-0 flex shadow-md shadow-black text-sm" style="background:black">
		<div class="flex-1 p-1" style="background:#262686">
			{{ $slidev.configs.title || "Unknown title" }}
		</div>
	</header>
</template>

<script setup lang="ts">
	import { computed } from "vue";

	import type { SlideInfoBase } from "@slidev/types";

	const sections = computed(() => {
		const result: [string, number[]][] = [];
		let pages: number[] = [];
		let title = "";
		for(let i = 1; i < $slidev.nav.slides.length; i++) {
			const slide = $slidev.nav.slides[i];
			const section = (slide.meta?.slide as SlideInfoBase)?.frontmatter?.section;
			if(section && section != title) {
				if(pages.length > 0) result.push([title, pages]);
				pages = [];
				title = section;
			}
			pages.push(i);
		}
		result.push([title, pages]);
		return result;
	});
</script>