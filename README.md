# social-media

This is a concept of using GitHub as a social media platform.

I just had this idea while walking on the streets and thought I'd write them down, evne though I probably won't be implementing it.

This README explains how each GitHub feature can contribute to making GitHub as a social media platform, along with some of my other thoughts. Because these are my raw thoughts quickly written down without any proper organization, it could be quite messy and have a lot of blabbering.

## Goal

The goal is to use as least external technologies as possible and use as much native GitHub features as possible to create a social media platform on GitHub. For example, making a static site that pulls information from this repo via GitHub API is not within the goal of this concept. However, building a GitHub bot to fill in features that are not natively supported by GitHub and assist the operation of the social media is acceptable.

## Features

### Creating Posts

Posts are made by creating issues in this repo.

Issues are easy to create, they can contain texts, links, images, and supports markdown natively, making them the perfect candidate for being used as posts.

Reactions can be made to posts by using the built-in reaction feature, although the number of reactions available is quite limited, I think it's sufficient.

Comments can be made to posts by adding a comment to the issue, note that comments can have reactions too.

Posts and comments can be edited using the native feature provided by GitHub. Interestingly, GitHub shows the edit histories of issue descriptions and issue comments, so this is quite useful (maybe for moderation purposes.)

### Following Users

Technically, the user can search posts created by a specific user using the issue search bar and filter by issue author. However, if a user wants to receive notification when the user they follow makes a new post, this will require a bot's help to make a comment under the post to mention all the people that follow the user.

### Tagging Topics

Simply add "#tag" into the issue description like "#summer", this makes the post appear when someone searches the tag.

### Mentioning Other Users & Posts

You can mention other users by using the built-in `@` syntax, this will also send a notification to them.

You can link to other posts by mentioning their issue numbers, like `#367`. This will make your post show up in the corresponding post, which could potentially be useful for maybe megathreads?

### Algorithm

This is the core of social medias, but honestly, I'm not sure if this is really needed for this concept. Since all the posts can be found in the issues page, and the user can use the powerful issue search bar to find posts they want, users can probably just [create views in the issues page](#searching) that have a specific combination of search filters to find posts they want. Essentially, each user can make a personalized algorithm for themselves.

Now, I'm not a social media expert, so if I were to make an algorithm to recommend posts, I don't know how to. Though, I can probably make it with the help of some existing projects.

One concept I have in mind is to use AI to categorize the topics a post is about. Then, if a user makes a reaction to the post, the "score" that user has for those topics will slightly increase. If the user makes a comment, the score will increase more. Finally, based on the score that each user has for each topic, recommend a newly created post to the corresponding users that are interested in the topic.

### Creating Instances

Anyone can create another instance of the social media by forking this repo. This could be used to, for example, making a dedicated space for a specific topic, like subreddits on Reddit.

One potential problem is that I'm not sure whether bots and CI/CD can work properly on forks like how they do on the original repo.

### Searching

The [GitHub issues](https://github.com/issues) page allows users to search issues based on filters, it even allows users to create and save a set of search filters, called "Views". For example, a user can create a view with the following filters: `is:open mentions:@me sort:created-desc repo:seriaai/social-media reactions:>10 AND (winter in:title OR summer in:title)`. This finds posts in the main instance with more than 10 reactions and has either "winter" or "summer" in the title. For more information, see GitHub's [documentation](https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests).

Because of how GitHub issues work, every single post made on the social media platform is searchable and visible. There are literally no hidden posts, which I personally think is better than traditional social medias, where posts are like needels in the ocean, and you can only find them if you're lucky enough for the algorithm to push them to you.

### Notifications

Users can subscribe to posts they are interested. I'm pretty sure GitHub also automatically subscribes for you when you make a reply.

## GitHub Features That Could be Useful

### Pull Requests

I originally imagined each user to create a pull request, which will be their "personalized feed". A bot will automatically comment issue links in the pull request that it thinks the user will be interested based on the algorithm. However, the major problem is that pull requests require code changes to be created, which makes it a lot less accesible than issues.

For now, I think pull requests will remain to be used as a way to contribute to the project itself like how it currently is intended for.

### Branches

I imagine each user in the social media can have their own branch, which will be their "personalized feed". A bot will run GitHub actions regularly to update each branch's README with the relevant issues that the user may be interested.

### Sub-Issues

This feature seems to have some huge potential, but I haven't thought of it yet.

### Labels

Issue labels are interesting, it seems like there isn't a hard limit to them (someone have created 10,000 labels.) They are searchable, and they can carry a color and a description along with the label name itself.

The only issue is that it's can't be applied by the issue creator themself, but rather by the repo maintainers. This is why I didn't use issue labels for tagging topics (well, writing tags manually are more flexible than issue labels, anyways.)

One possible usage is use issue labels to flag posts that are popular, like how Pixiv put labels on artworks that exceed a certain number of likes.

### Issue Templates

This can be useful for those who create an instance of the original repo to limit the way user posts in the "subreddit", for example adding a flair to add issue labels to the post.

Also, issue templates act like forms, it can even have buttons and dropdown menus, so this seems to be something that can have a huge potential. For example, UI elements that can interact with the GitHub bot.

Issue templates can also be generated/edited dynamically using GitHub Actions.
