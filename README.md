# Alien::Nettle [![Build Status](https://secure.travis-ci.org/plicease/Alien-Nettle.png)](http://travis-ci.org/plicease/Alien-Nettle)

Find or build nettle low-level cryptographic library

# SYNOPSIS

In your Build.PL:

    use Module::Build;
    use Alien::Nettle;
    my $builder = Module::Build->new(
      ...
      configure_requires => {
        'Alien::Nettle' => '0',
        ...
      },
      extra_compiler_flags => Alien::Nettle->cflags,
      extra_linker_flags   => Alien::Nettle->libs,
      ...
    );
    
    $build->create_build_script;

In your Makefile.PL:

    use ExtUtils::MakeMaker;
    use Config;
    use Alien::Nettle;
    
    WriteMakefile(
      ...
      CONFIGURE_REQUIRES => {
        'Alien::Nettle' => '0',
      },
      CCFLAGS => Alien::Nettle->cflags . " $Config{ccflags}",
      LIBS    => [ Alien::Nettle->libs ],
      ...
    );

# DESCRIPTION

This distribution provides Nettle so that it can be used by other 
Perl distributions that are on CPAN.  It does this by first trying to 
detect an existing install of Nettle on your system.  If found it 
will use that.  If it cannot be found, the source code will be downloaded
from the internet and it will be installed in a private share location
for the use of other modules.

# SEE ALSO

[Alien](https://metacpan.org/pod/Alien), [Alien::Base](https://metacpan.org/pod/Alien::Base), [Alien::Build::Manual::AlienUser](https://metacpan.org/pod/Alien::Build::Manual::AlienUser)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
