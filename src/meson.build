sigcxx = dependency('sigc++-2.0')
pixman = dependency('pixman-1')
physfs = dependency('physfs', version: '>=2.1')
vorbisfile = dependency('vorbisfile')
sdl2 = dependency('sdl2')
sdl2_ttf = dependency('SDL2_ttf')
sdl2_image = dependency('SDL2_image')
sdl_sound = dependency('SDL_sound')
opengl = dependency('GL')

boost = dependency('boost', version: '>=1.49', modules: 'program_options')
openal = dependency('openal')
zlib = dependency('zlib')

main_dependencies = [sigcxx, openal, opengl, boost, zlib, pixman, physfs, vorbisfile, sdl2, sdl2_ttf, sdl2_image, sdl_sound]
if host_system == 'darwin'
    main_dependencies += compiler.find_library('iconv')
    main_dependencies += dependency('CoreFoundation')

    if openal.type_name() != 'pkgconfig'
    add_project_arguments('-DUSE_MAC_OPENAL', language: 'cpp')
    endif
elif host_system == 'windows'
    main_dependencies += compiler.find_library('wsock32')
endif

if get_option('shared_fluid') == true
    fluidsynth = dependency('fluidsynth')
    add_project_arguments('-DSHARED_FLUID', language: 'cpp')
    main_dependencies += fluidsynth
endif

if get_option('default_framerate') == true
    add_project_arguments('-DDEFAULT_FRAMERATE', language: 'cpp')
endif

if get_option('cjk_fallback_font') == true
    add_project_arguments('-DCJK_FALLBACK', language: 'cpp')
endif

main_headers = files(
    'quadarray.h',
    'audio.h',
    'binding.h',
    'bitmap.h',
    'disposable.h',
    'etc.h',
    'etc-internal.h',
    'eventthread.h',
    'flashable.h',
    'font.h',
    'input.h',
    'iniconfig.h',
    'plane.h',
    'scene.h',
    'sprite.h',
    'table.h',
    'texpool.h',
    'tilequad.h',
    'transform.h',
    'viewport.h',
    'window.h',
    'serializable.h',
    'shader.h',
    'glstate.h',
    'quad.h',
    'tilemap.h',
    'tilemap-common.h',
    'graphics.h',
    'gl-debug.h',
    'global-ibo.h',
    'exception.h',
    'filesystem.h',
    'serial-util.h',
    'intrulist.h',
    'binding.h',
    'gl-util.h',
    'util.h',
    'config.h',
    'settingsmenu.h',
    'keybindings.h',
    'tileatlas.h',
    'sharedstate.h',
    'al-util.h',
    'boost-hash.h',
    'debugwriter.h',
    'gl-fun.h',
    'gl-meta.h',
    'vertex.h',
    'soundemitter.h',
    'aldatasource.h',
    'alstream.h',
    'audiostream.h',
    'rgssad.h',
    'windowvx.h',
    'tilemapvx.h',
    'tileatlasvx.h',
    'sharedmidistate.h',
    'fluid-fun.h',
    'sdl-util.h',
    'lang-fun.h'
)

main_source = files(
    'main.cpp',
    'audio.cpp',
    'bitmap.cpp',
    'eventthread.cpp',
    'filesystem.cpp',
    'font.cpp',
    'input.cpp',
    'iniconfig.cpp',
    'plane.cpp',
    'scene.cpp',
    'sprite.cpp',
    'table.cpp',
    'tilequad.cpp',
    'viewport.cpp',
    'window.cpp',
    'texpool.cpp',
    'shader.cpp',
    'glstate.cpp',
    'tilemap.cpp',
    'autotiles.cpp',
    'graphics.cpp',
    'gl-debug.cpp',
    'etc.cpp',
    'config.cpp',
    'settingsmenu.cpp',
    'keybindings.cpp',
    'tileatlas.cpp',
    'sharedstate.cpp',
    'gl-fun.cpp',
    'gl-meta.cpp',
    'vertex.cpp',
    'soundemitter.cpp',
    'sdlsoundsource.cpp',
    'alstream.cpp',
    'audiostream.cpp',
    'rgssad.cpp',
    'vorbissource.cpp',
    'windowvx.cpp',
    'tilemapvx.cpp',
    'tileatlasvx.cpp',
    'autotilesvx.cpp',
    'midisource.cpp',
    'fluid-fun.cpp',
    'lang-fun.cpp'
)

main = [main_source, main_headers]

if get_option('use_fakeapi') == true
    main += files('fake-api.cpp', 'fake-api.h')
endif

if discord == true
    main += files('discordstate.cpp', 'discordstate.h')
endif
