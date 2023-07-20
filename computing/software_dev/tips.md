# Programming Tips

This is a list of general tips about programming and software development. The list isn't in any specific order.

This list also doubles as a reference for topics that I may want to write full articles about at some point.

## Random Meta Stuff

- If it isn't documented, it isn't done
- Documentation isn't just for others, it's for you, too!
- *Always* use version control
- Don't be afraid to ask for help
- [Plan to Throw One Away](https://course.ccs.neu.edu/cs5500f14/Notes/Prototyping1/planToThrowOneAway.html)
- IRC is a great resource
- Make it work, then make it fast, then make it pretty
- Rubber ducks are your friend
- Remember to take breaks
- Fix your posture!
- Rest your eyes every so often
- Use a blue light filter
- Learn to use your tools properly, but don't become too dependent on specific ones
- Solve problems on paper first
- Be transparent
- Write code as if your successor knows where you live
- TODO never gets done
- Don't try to over-engineer everything
- Don't just think about code, but about data structures and their relationships
- The amount of RAM you *think* you need is wrong
- Remember to write unit and integration tests!

## Gamedev-Specific

- Collisions
    - To get the side of a collision, separate the x and y axis (makes the math easier)
        1. Move an object on the x axis
        2. Check for horizontal collisions
        3. Move the object on the y axis
        4. Check for vertical collisions
     - Figuring out where a colliding object came from
         - Position-based collision
             - Check current position of each object as well as the position on the previous frame
             - For each direction: is there a collision for this side and was there no collision on this side on the last frame?
             - This way, we don't have to worry about direction