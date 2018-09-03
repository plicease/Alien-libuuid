# Alien::libuuid [![Build Status](https://secure.travis-ci.org/plicease/Alien-libuuid.png)](http://travis-ci.org/plicease/Alien-libuuid)

Find or download and install libuuid

# SYNOPSIS

In your Build.PL:

    use Module::Build;
    use Alien::libuuid;
    my $builder = Module::Build->new(
      ...
      configure_requires => {
        'Alien::libuuid' => '0',
        ...
      },
      extra_compiler_flags => Alien::libuuid->cflags,
      extra_linker_flags   => Alien::libuuid->libs,
      ...
    );
    
    $build->create_build_script;

In your Makefile.PL:

    use ExtUtils::MakeMaker;
    use Config;
    use Alien::libuuid;
    
    WriteMakefile(
      ...
      CONFIGURE_REQUIRES => {
        'Alien::libuuid' => '0',
      },
      CCFLAGS => Alien::libuuid->cflags . " $Config{ccflags}",
      LIBS    => [ Alien::libuuid->libs ],
      ...
    );

# DESCRIPTION

This distribution provides libuuid so that it can be used by other 
Perl distributions that are on CPAN.  It does this by first trying to 
detect an existing install of libuuid on your system.  If found it 
will use that.  If it cannot be found, the source code will be downloaded
from the internet and it will be installed in a private share location
for the use of other modules.

# SEE ALSO

[Alien](https://metacpan.org/pod/Alien), [Alien::Base](https://metacpan.org/pod/Alien::Base), [Alien::Build::Manual::AlienUser](https://metacpan.org/pod/Alien::Build::Manual::AlienUser)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2018 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
