# 🧠 Useful Prompts

## Internacionalization for Nextjs (Use after setup of the dict provider)

move the hardcoded strings to pt.json, en.json and es.json dict. It might be hardcoded strings on nested component (specially for server component). follow these rules. If its a nextjs server component, load the dict from. 

import { getDictionary } from "@/dictionaries/dictionaries"; (top import)

then get the lang from the params like that:
export default async function LandingPage({
  params,
}: {
  params: Promise<{ lang: "en" | "es" | "pt" }>;
}) {
  const { lang } = await params;
  const dict = await getDictionary(lang);
...

for client components, use the provider. DO NOT pass down the dict as props. Example usage might be:

"use client";
import { useDict } from "@/providers/dictionary-provider";

then inside component get the dicy by
const dict = useDict();

then you just have to use
dict.section.stringtouse
