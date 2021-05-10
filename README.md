# Alien::libuuid ![linux](https://github.com/plicease/Alien-libuuid/workflows/linux/badge.svg) ![macos](https://github.com/plicease/Alien-libuuid/workflows/macos/badge.svg)

Find or download and install libuuid

# SYNOPSIS

In your Makefile.PL:

```perl
use ExtUtils::MakeMaker;
use Alien::Base::Wrapper ();

WriteMakefile(
  Alien::Base::Wrapper->new('Alien::libuuid')->mm_args2(
    # MakeMaker args
    NAME => 'My::XS',
    ...
  ),
);
```

In your Build.PL:

```perl
use Module::Build;
use Alien::Base::Wrapper qw( Alien::libuuid !export );

my $builder = Module::Build->new(
  ...
  configure_requires => {
    'Alien::libuuid' => '0',
    ...
  },
  Alien::Base::Wrapper->mb_args,
  ...
);

$build->create_build_script;
```

In your [FFI::Platypus](https://metacpan.org/pod/FFI::Platypus) script or module:

```perl
use FFI::Platypus;
use Alien::libuuid;

my $ffi = FFI::Platypus->new(
  lib => [ Alien::libuuid->dynamic_libs ],
);
```

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

Author: Graham Ollis <plicease@cpan.org>

Contributors:

Thibault Duponchelle (tib)

# COPYRIGHT AND LICENSE

This software is copyright (c) 2018 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
