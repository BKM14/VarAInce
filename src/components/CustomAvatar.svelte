<script lang="ts">
	import { Avatar } from "flowbite-svelte";
    
    export let profile: Profile;
</script>

<script context="module" lang="ts">
    export interface Profile {
        image: string;
        imageAlt: string;
        name: string;
        post: string;
    }
</script>

<div class="text-center">
    <Avatar src={profile.image} alt={profile.imageAlt} class="w-23 h-22 lg:w-38 lg:h-36 mx-auto"/>
    <div class="text-white font-bold">{profile.name}</div>
    <div class="text-white font-light">{profile.post}</div>
</div>