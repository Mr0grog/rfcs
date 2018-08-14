- Feature Name: dataset_naming
- Start Date: 
- RFC PR: 
- Issue: NA

# Summary
[summary]: #summary

Define the qri naming system and conventions for name resolution.

# Motivation
[motivation]: #motivation

Why are we doing this? What use cases does it support? What is the expected outcome?

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

It’s possible to refer to a dataset in a number of ways. It’s easiest to look 
at the full definition of a dataset reference, and then show what the “defaults” 
are to make sense of things. The full definition of a dataset reference is 
as follows:

    dataset_reference = peer_name/dataset_name@/network/hash

an example of that looks like this:

    b5/comics@QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y/ipfs/QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y

In a sentence: b5 is the name of a peer, who has a dataset named comics, and 
it’s hash on the ipfs network at a point in time was `QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y`

We need peer names so lots of people can name datasets the same thing, and in 
this instance that giant hash thing is used to refer to a dataset at a specific 
version of a dataset, from an exact point in time.
default to latest on ipfs

Now, having to type b5/comics@/ipfs/QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y 
every time you wanted a dataset would be irritating. So we have two defaults. 
The default network is ipfs, and the default hash is the lastest known version 
of a dataset. We say latest known because sometimes things can fall out of sync. 
If you’r only working with your own local datasets, this won’t be an issue.

Anyway, that means we can cut down on the typing if we just want the latest 
version of b5’s comics dataset, we can just type:

b5/comics

In a sentence: “the latest version of peers b5’s dataset named comics.”
the me keyword

What if your peername is, say, golden_pear_ginger_pointer? First, why did you pick such a long peername? 
Whatever your answer it would be irritating to have to type your username every time, so we give you a special way to refer to yourself: me. So if you have a dataset named comics, you can just type:

me/comics

In a sentence: “the latest version of my dataset named comics.” Under the hood, we’ll re-write your request to your peername for you.
drop names with hashes

Finally, it’s also possible to use just the hash. This is a perfectly valid dataset reference:

/ipfs/QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y

In this case we’re ignoring naming altogether and simply referring to a dataset by it’s network and hash. Because IPFS hashes are global, we can do this across the entire network. If you’re coming from git, this is a fun new trick.
To recap:

All of these are ways to refer to a dataset:

    peer_name/dataset_name : b5/comics
    network/hash : /ipfs/QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y
    peer_name/dataset_name@/network/hash: b5/comics@/ipfs/QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y


# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

TODO 

# Drawbacks
[drawbacks]: #drawbacks

TODO

# Rationale and alternatives
[rationale-and-alternatives]: #rationale-and-alternatives

TODO

# Prior art
[prior-art]: #prior-art

TODO

# Unresolved questions
[unresolved-questions]: #unresolved-questions

TODO