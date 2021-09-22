<div id="music-player" class="music music__player">
  <audio style="display: none" id="music-audio" src="https://raw.githubusercontent.com/miko-github/miko-github/gh_assets/assets/sounds/Homayoun%20Shajarian%20-%20Arayeshe%20Ghaliz.mp3" preload="metadata" volume="0.2"></audio>
  <input type="file" multiple class="music__uploader" name="file-audio" id="file-audio" accept="audio/*" />
  <div class="music__controller">
    <button id="music-backward" title="backward" class="music__btn music__btn--back">
      <!-- ALT : fa-[step, fast, ]-backward -->
      <i class="fa fa-fast-backward"></i>
    </button>
    <button id="music-play" title="play" class="music__btn music__btn--play">
      <i class="fa fa-play"></i>
    </button>
    <button id="music-forward" title="forward" class="music__btn music__btn--next">
      <!-- ALT : fa-[step, fast, ]-forward -->
      <i class="fa fa-fast-forward"></i>
    </button>
  </div>
  <div class="music__main">
    <div id="music-playlist" class="music__playlist">
      <button type="button" id="playlist-close-btn" class="playlist__close_btn">
        <i class="fa fa-times"></i>
      </button>
      <ul class="playlist__track_list" id="playlist-tracks" tabindex="0"></ul>
    </div>
    <div class="music__meta">
      <div class="music__name">
        <h3 id="music-title" class="music__title">Arayeshe Ghaliz</h3>
        <span id="music-desc" class="music__description">
          Homayoun Shajarian
        </span>
      </div>

      <div class="music__mixin">
        <!-- STATE : --[off | on: [once | all]] -->
        <button id="music-repeat" class="music__repeat music__repeat--on music__repeat--all">
          <!-- ALT : fa-[repeat, sync, sync-alt, retweet, retweet-alt, redo, redo-alt] -->
          <i class="fa fa-repeat"></i>
        </button>
        <!-- STATE : --[off | on] -->
        <button id="music-shuffle" class="music__shuffle">
          <i class="fa fa-random"></i>
        </button>
        <!-- STATE : --[off | on] -->
        <button id="music-playlist-open" class="music__playlist_open">
          <i class="fa fa-list-music"></i>
        </button>
      </div>
      <div class="music__volume" title="50%">
        <button id="music-volume-btn" class="music__volume_btn">
          <i class="fa fa-volume"></i>
        </button>
        <div id="music-volume" class="music__volume_range">
          <span class="music__volume_handle"></span>
        </div>
      </div>

      <div class="music__times">
        <div id="music-seek" class="music__seek">
          <span class="music__seek_handle"></span>
        </div>
        <span id="music-current-time" class="music__current_time">
          00:00:00
        </span>
        <span id="music-duration" class="music__duration">02:33</span>
      </div>
    </div>
    <div class="music__cover">
      <img id="music-cover" class="music__image" src="https://www.ganja2music.com/Image/Post/06.93/08/Homayoun-Shajarian---Arayes.jpg" alt="mini music player - miko-github" />
    </div>
  </div>
</div>

<!-- <style lang="scss">
/* powered by yek-sass */
$_background: #d3dcdd;
$_cool-background: #eaf2ff;
$_cool-white: #f9fcff;
$_cool-sky: #add8e6;
$_cool-blue: #5c9dc0;
$_cool-green: #bdb369;
$_cool-black: #002e63;
$_cool-silver: #eeeeee;
$_cool-gray: darken(#dbdcdb, 25);
$_description: #8c9294;
$_btn-hover: #e5eff9;
$_icon-hover: $_cool-blue;
:root {
  --seek_listener_percentage: 0%;
  --volume_listener_percentage: 50%;
}

body {
  @include yek-aligns;
  background-color: $_background;
}

/* +++ MAIN +++ */
.music {
  @include yek-flex;
  @include yek-size(530px, 180px);
  @include yek-aligns;
  position: relative;
  border: 4px desaturate($_cool-white, 45%) solid;
  overflow: hidden;
  background-color: $_cool-white;
  box-shadow: 0 4px 7px rgba($_cool-black, 0.3);

  & {
    border-radius: 8px;
  }
  &__main {
    @include yek-flex;
    @include yek-size(unquote("#{(54.5 + 35)}%"), 100%);
    position: relative;
    padding: 0;
    margin: 0;
  }
  &__image {
    border-top-right-radius: 6px;
    border-bottom-right-radius: 6px;
  }
}

/* +++ METADATA +++ */
.music {
  &__meta {
    @include --ellipsis;
    @include yek-flex;
    @include yek-size(60.8%, 100%);
    padding: 6px 24px;
  }
  &__name {
    @include yek-flex;
    // TOGGLE @include yek-aligns(flex-start);
    @include yek-size(100%, calc(100% - 80px));
  }
  &__title,
  &__description {
    @include --ellipsis;
    @include yek-width(100%);
    padding: 6px 0;
  }
  &__title {
    margin: 0;
  }
  &__description {
    font-size: 0.8rem;
    color: darken($_cool-gray, 25);
  }

  &__cover {
    @include yek-size(39.2%, 100%);
    @include yek-flex;
    @include yek-aligns;
  }
  &__image {
    @include --image-cover;
  }
}

/* +++ UPLOAD +++ */
.music {
  &--upload::before,
  &--upload::after {
    display: block;
    position: absolute;
    background: $_cool-white;
  }
  &--upload::after {
    @include yek-size;
    content: "";
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    z-index: 90;
  }
  &--upload::before {
    $posy: calc(5% - 0px);
    $posx: calc(2.5% - 0px);
    @include yek-size(95%, 90%);
    content: "DROP HERE...";
    top: $posy;
    bottom: $posy;
    left: $posx;
    right: $posx;
    border: 5px dashed $_cool-blue;
    border-radius: 9px;
    line-height: 5;
    text-align: center;
    vertical-align: middle;
    font-size: 2rem;
    font-weight: 800;
    color: $_cool-black;
    z-index: 95;
  }

  &__uploader {
    @include yek-size;
    display: none;
    position: absolute;
    left: 0;
    right: 0;
    top: -100%;
    bottom: 100%;
    opacity: 0;
    background: #fff;
    // will-change: top, bottom, display;

    &--show {
      display: block;
      top: 0;
      bottom: 0;
      z-index: 99;
    }
  }
}

/* +++ CONTROLLERS +++ */
.music {
  &__controller {
    @include yek-size(10.5%, 100%);
    @include yek-flex(column);
  }

  &__btn {
    @include --clear-btn;
    @include yek-size(100%, 33.33%);
    cursor: pointer;
    background-color: transparent;

    & i {
      padding: 12px;
      border-radius: 5px;
      will-change: text-shadow, box-shadow, transform, background-color, color,
        padding-right, padding-left;
    }
    &--pause i {
      // NOTE : exact center
      padding-left: 14px;
      padding-right: 12px;
    }
    // TOGGLE : `&:hover { background-color: $_btn-hover; }`
    &:hover i {
      transform: scale(1.2);
      color: $_icon-hover;
      background-color: $_cool-silver;
    }
    &:active i {
      transform: scale(0.9);
    }
  }
}

// TODO : build, this option

/* +++ MIXINS +++ */
@mixin --clear-btn-2 {
  transform: scale(0.85);
  transition-property: transform;
  cursor: pointer;
  &:hover i {
    transform: scale(1.2);
    background-color: $_cool-silver;
  }
  &:active i {
    transform: scale(0.9);
  }
}
.music {
  &__mixin,
  &__volume {
    @include yek-size(50%, 35px);
    @include yek-flex;
  }

  &__mixin {
    @include yek-aligns(space-between);
    margin-left: -6px;
  }

  &__volume_btn,
  &__shuffle,
  &__repeat,
  &__playlist_open {
    @include --clear-btn;
    @include --clear-btn-2;
    @include yek-height(25px);
    background-color: transparent;

    & i {
      // font-size: 0.8rem;
      padding: 8px;
      border-radius: 9px;
      will-change: transform, background-color, color, padding-right,
        padding-left;
    }
    &--on i {
      color: $_icon-hover;
    }
  }

  &__shuffle,
  &__repeat,
  &__playlist_open {
    @include yek-width(33.33%);
  }
}

/* +++ SEEK/TIMES +++ */
.music {
  &__times {
    @include yek-flex;
    @include yek-aligns(space-between);
    @include yek-size(130%, 25px);
    // TODO : if neccery `transform: translateY(-20px);`
    color: $_cool-gray;
  }
  &__duration,
  &__current_time {
    @include yek-size(45%);
    @include --ellipsis;
  }
  &__times,
  &__duration,
  &__current_time {
    padding: 0;
    margin: 0;
    font-size: 0.8rem;
  }
  &__duration {
    text-align: right;
    padding-right: 5px;
  }
  &__current_time {
    text-align: left;
    padding-left: 2px;
  }
  &__seek {
    @include yek-width(100%);
    background-color: $_cool-sky;
  }
  &__seek_handle {
    @include yek-width(var(--seek_listener_percentage));
    display: block;
    background-color: $_cool-blue;
  }
  &__seek,
  &__seek_handle {
    @include yek-height(3px);
    border-radius: 9px;
    transition-timing-function: ease-in-out;
    cursor: pointer;
    will-change: height;
  }
  &__seek:hover,
  &__seek:hover &__seek_handle {
    @include yek-height(5px);
  }
}

/** +++ VOLUME +++ **/
.music {
  &__volume {
    @include yek-aligns;
  }

  &__volume_btn {
    @include yek-width(30%);
    transform: translate(-7px, -25%);
  }
  &__volume_range {
    @include yek-size(60%);
    transform: translateY(-70%);
    background-color: $_cool-sky;
  }
  &__volume_handle {
    @include yek-width(var(--volume_listener_percentage));
    display: block;
    background-color: $_cool-blue;
  }
  &__volume_range,
  &__volume_handle {
    @include yek-height(3px);
    border-radius: 9px;
    transition-timing-function: ease-in-out;
    cursor: pointer;
  }
}

/* +++ PLAYLIST +++ */
.music {
  &__playlist {
    transition: 0.3s;
    @include absolute(100%, 0, 100%, 0);
    z-index: 70;
    display: none;

    &--open,
    &--on {
      display: block;
      @include yek-flex;
      top: 0;
      bottom: 0;
      background: $_cool-silver;
    }
  }
}
.music__playlist,
.playlist__track_list {
  overflow: hidden;
}
.playlist__track_list {
  @include --clear-list;
  overflow-y: auto;
}
$--track-size: 90px;
$--cover-size: 70px;
.playlist {
  &__close_btn {
    @include --clear-btn;
    @include --clear-btn-2;
    @include absolute(5px);
  }
  &__track_list {
    @include yek-size;
    @include yek-flex;
    @include yek-align(space-around, flex-start, flex-start);
    &:focus {
      @include --clear-btn;
    }
  }

  &__track {
    @include yek-flex;
    @include yek-size(90%, $--track-size);
    background-color: $_cool-white;
    margin: 9px auto;
    padding: 10px;
    border-radius: 15px;
    &:hover {
      background-color: $_btn-hover;
      cursor: pointer;
    }
    &--current {
      background: bisque;
    }
  }

  &__cover {
    @include --image-cover;
    @include yek-size($--cover-size, $--cover-size);
    border-radius: 9px;
  }

  &__meta {
    @include yek-flex(column);
    @include yek-size(calc(100% - $--cover-size), 100%);
    @include yek-align(space-between, flex-start, flex-start);
    padding: 9px;
  }

  &__title,
  &__artist {
    @include --ellipsis;
    @include yek-width;
  }
}
</style> -->