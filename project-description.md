# Test Project Outline – Module E – Virtual World Interactive Game

## Competition time

4 hours

## Introduction

In this project, we would like to create a game for kids learning.

It is a simple virtual world. Player can control the avatar to move left
and right. And progress to different scenes while moving to the left
edge or right edge of the game screen.

The game can be toggled into full-screen, without seeing the task bar
and browser UI.

## General Description of Project and Tasks

This project involves creating an interactive web-based game for educational purposes. The game features a virtual world where players control an avatar to navigate through different scenes while engaging with learning activities and quizzes.

The game must be accessible via the path `/XX_module_e/` where XX is the workstation number and include the following core features:

- **Avatar Movement**: Keyboard and touch/mouse control with position persistence
- **Scene Management**: Multiple interconnected scenes with smooth transitions
- **Interactive Objects**: Clickable game objects with sound effects and animations
- **Learning Activities**: Educational quizzes that block progression until completed
- **Full-screen Support**: Toggle between windowed and full-screen modes
- **API Integration**: Score reporting to external game platform

The implementation should use web technologies (HTML, CSS, JavaScript) with consideration for code quality and user experience.

![](media/image1.jpg){width="6.6930555555555555in" height="4.16875in"}

## Requirements

### Scene Construction

For each scene, the bottom part is area where avatar may move. The upper
part of the scene is constructed by different scene objects.

There are seneral object types per scene, they are:

- main activity area

- right game objects, with slightly parallax effect.

- other game objects.

- quiz barriers on the avatar-moving area on right edge of the screen.

When avatar moves to the right edge, and touch or near to the quiz
barrier, the corresponding quiz shows.

During the video playback, the the video should play inline while in PC.

Scene creation has animation to present the scene objects one by one.
Please don't make the animation too slow that cannot be assessed.

### Special Game Objects in the Scene

There are different game objects designed for the scene. They are
prepared when in the media files, grouped by folder named for each
scene.

You can refer to the media files on the placements of the game objects
for each scene.

The scene document in media files also describes the z-index for each
game objects provided. Please follow it when constructing the scene.

Here are some special game objects that provide interactivity:

- Learning activities barriers o There are learning activity barriers on
  the road, blocking the road.

  - Avatar cannot go through these barriers. The avatar need to clear
    the barriers on the roads before they can move to the next scene by
    reaching the right edge of the screen.

  - The learning activity dialog shows when either the following
    happens:

    - When the avatar moves and hits the barrier.

    - or When the player directly click or tap on the barrier,
      regardless of the avatar's current position.

  - When hitting the activity barriers by the avatar, the activity show
    in a dialog.

  - (Hitting means the avatar is very close to the barrier visually)

  - Please refer to the learning activities details description in this
    document for details on what's showing up.

  - When the learning activities shows, the "learning-activity" sound
    effect is played.

- Main activity object, either a video or an image o When user click or
  tap on the videos, the video plays, inline in the embed player o When
  scene contains no video, there is an image in the middle area of
  scene.

- Parallax rotation on the object at right-hand side of the scene o When
  the mouse over on this object, there is parallax effect. See details
  below.

- Other game objects o When clicking or tapping on other game objects,
  the "object-sound" sound effect is played. o Clicking on the scene
  objects on screen will animate the object a little bit, in any forms.

### Parallax Game Objects

In the scene, there may be at most one object that has subtle parallax
rotation effect.

The objects with parallax effect should have good feeling of parallax.

Giving the parallax effect may be fine tuned by the animation experts,
the amount of parallax feeling should be easily configured in code for
non-prorgrammers to adjust.

One example of the parallax game effect is recorded in the media file.

### Interactivity: Sound

Clicking on the designed objects produces specific sound. Sound files
can be found in media files.

Clicking on the scene objects on screen will animate the object a little
bit, in any forms.

### Avatar Movement

Player can control and the avatar by keyboard and directly
clicking/tapping on the game screen.

When using keyboard, player can press the arrow keys to move the avatar.
When using touch screen, player can tap the screen to move the avatar
directly to that position, unless the tapped area is not able to walk
on.

When using mouse, player can click on the area and the behavior is
similar to the tapping of the screen.

When tapping or clicking on the screen, an animation should show the
clicked/tapped point to showcase the point where the avatar is heading
to.

The avatar position is saved via LocalStorage. And the avatar position
can be resumed when web page loads or refresh.

### Scene Switching

When the avatar moves to the left/right of the screen, the scene changes
to the next/previous scene. If there is unfinished quiz barrier, the
avatar can't move to the right edge of the scene. Thus player cannot
change scene until finishing all quiz barriers.

During the scene switching, the scene objects in current scenes goes out
with transition and the new scene comes out with transition too.

### Learning Activity: Quiz

Quiz learning activity happens when the avatar hits the quiz barrier.
The quiz shows a text-only multiple choice, fourchoose-one.

The quiz showing should be animated with energtic feeling to provide not
boring experience to the yound readers that is learning. Seleting any
choices should also give an energetic feeling of animation.

The quiz stays when the selection is incorrect. The quiz goes away and
the quiz barrier is removed after choosing correct answer.

### Use of API

This game will be uploaded to the game platform. So it uses the API
provided by the game platform. After the game ends while player
finishing all quizzes, the count of total correct quizzes (equal to the
amount of quizzes) is post to the game platform via the score saving
API. Please show an error if the score saving fails.

API reference:

The message the game has to send to the parent via
\`window.parent.postMessage(\...)\` looks like this:

{

\"event_type\": \"game_run_end\",

\"score\": 100

}

### Instructions to the Competitor

- Project should be accessible via /XX_module_e/ where XX is the
  workstation number.

- All assessment is done on server. No assessment process in
  workstation.

- You should consider the quality of code.

## Assessment

The project will be assessed on a server environment. All assessment will be conducted on the server, with no assessment process required on the workstation.

Evaluation will focus on:

- **Functionality**: All game features work as specified
- **Code Quality**: Clean, well-structured, and maintainable code
- **User Experience**: Smooth interactions and appropriate feedback
- **Technical Implementation**: Proper use of web technologies and APIs

Assessment tools and browsers will be used to verify compliance with the technical requirements and game mechanics.

## Mark distribution

| WSOS SECTION | Description | Points |
|--------------|-------------|---------|
| 1 | Work organization and self-management | 0.5 |
| 2 | Communication and interpersonal skills | 0.5 |
| 3 | Design implementation | 4.25 |
| 4 | Front-end development | 7.5 |
| 5 | Back-end development | 3.25 |
| **Total** | | **16** |

### Detailed Breakdown

| Task | Description | Communication | Design | Layout | Front-end | Total |
|------|-------------|---------------|---------|---------|-----------|-------|
| E1 | Avatar movement | 0.5 | 0.5 | - | 4 | 5 |
| E2 | Scene construction and switching | - | 1.75 | 0.75 | 1.5 | 4 |
| E3 | Learning Activities | - | 2 | 3 | 2 | 7 |
| **Total** | | **0.5** | **4.25** | **3.75** | **7.5** | **16** |
