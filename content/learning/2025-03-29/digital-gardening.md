## Setting up a quartz obsidian digital garden
Working from the [getting started instructions](https://quartz.jzhao.xyz/), this site will be [publicly hosted on github](https://github.com/stocad/garden-stocad-com). Different from the instructions, I would like to host this site on [AWS Amplify hosting](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html) which I will document below.

The basic idea here is to host public only content in the digital gardening. [^1][^2] Content will be evergreen, I like the idea of keeping a password protected garden compiled out of a private vault/repo as a way to separate out the personal, directly connected to me content from more evergreen public content. I don't aspire to turn this content into a book or a monetary.

This raises the question of content rights. For the moment, I am adding the CC BY-NC-SA[^3] license to the footer. I think this best captures the intent of what I'm doing.

I'm tempted to launch into a ramble about no-motes, no-kings, but I'll plant those as [[seedlings]] for another time.

Alright, lets get this up on the internet before I get lost down any other rabbit trails.

1. Create a new Amplify application.
2. Select the Github repository with my initial commit
3. Give the app a name
4. Frontend build command: `npx quartz build`
5. Build output directory: `public`
6. Click through to Save and Deploy

At this point Amplify failed to deploy with the error:
```
Amplify engine Not compatible with your version of node/npm: @jackyzha0/quartz@4.5.0
...
npm ERR! notsup Required: {"npm":">=9.3.1","node":">=20"}
```

Reading around online this can be resolved by using `nvm` to set the node version during pre-build.

So...  In the AWS Amplify console, under the application I:
- Went to Hosting > Build settings
- Changed preBuild to the following:
```yml
	...
		 preBuild:
			commands:
                - 'nvm install 20'
                - 'nvm use 20'
                - 'npm ci --cache .npm --prefer-offline'
    ...
```

This deploys. Great!  Now I have an arbitrary Amplify url and I need to map garde.stocad.com to this build process.

Back in the AWS Amplify App console, under Hosting > Custom domain.
1. Select the domain name to connect
	1. This tries to use Route 53, but I'm using cloudflare, so I need to copy the DNS info across to cloudflare for this to work
2. Once added, under Actions > View DNS Records
3. Open Cloudflare and copy both the verify and subdomain records across to Cloudflare (or wherever you manage DNS)
4. And, after a minute of waiting and an odd resolution error message, [there it is](https://garden.stocad.com/)!

[^1]: https://obsidian.rocks/creating-a-digital-garden-in-obsidian/
[^2]: https://jzhao.xyz/posts/networked-thought#what-is-digital-gardening
[^3]: https://creativecommons.org/licenses/by-nc-sa/4.0/
