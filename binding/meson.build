
ver = get_option('mri_version')
binding_dependencies = []
if ver.version_compare('>1.8') == true
    binding_dependencies += dependency('ruby-' + ver)
else
    lib = get_option('ruby_lib')
    binding_dependencies += compiler.find_library(lib)
    add_project_arguments('-DOLD_RUBY', language: 'cpp')
endif

if get_option('no_preload_scripts') == true
    add_project_arguments('-DNO_PRELOAD_SCRIPTS', language: 'cpp')
endif

binding_headers = files(
    'binding-util.h',
    'binding-types.h',
    'serializable-binding.h',
    'disposable-binding.h',
    'sceneelement-binding.h',
    'viewportelement-binding.h',
    'flashable-binding.h',
)

binding_source = [files(
    'binding-mri.cpp',
    'binding-util.cpp',
    'table-binding.cpp',
    'etc-binding.cpp',
    'bitmap-binding.cpp',
    'font-binding.cpp',
    'graphics-binding.cpp',
    'input-binding.cpp',
    'sprite-binding.cpp',
    'viewport-binding.cpp',
    'plane-binding.cpp',
    'window-binding.cpp',
    'tilemap-binding.cpp',
    'audio-binding.cpp',
    'module_rpg.cpp',
    'filesystem-binding.cpp',
    'windowvx-binding.cpp',
    'tilemapvx-binding.cpp',
    'miniffi-binding.cpp'
)]

if discord == true
    binding_source += files('discord-binding.cpp')
endif

bindings = [binding_headers, binding_source]
