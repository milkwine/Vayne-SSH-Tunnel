# NAME

Vayne::SSH::Tunnel - SSH tunnel wrapper

# SYNOPSIS

    use Vayne::SSH::Tunnel;

    Vayne::SSH::Tunnel::Run
    (
        name           => 'tunnel_foo',
        title          => 'title_to_generate',
        confdir        => '/tmp/tun',
        dport          => 9999,
        way            => [ 'nobody@ser1.com', 'nobody@ser2.com', 'nobody@ser3.com' ],
        user           => 'nobody',
        option         => ['ServerAliveInterval=10', 'ServerAliveCountMax=3', 'StrictHostKeyChecking=no'],
        timeout        => 600,
        max_channel    => 50,
        grep_word      => {
            'open failed'           => 10,
            'cannot listen to port' => 1,
        },
    );

# DESCRIPTION

Vayne::SSH::Tunnel is SSH tunnel wrapper.

Find a free port to do the ssh tunnel using 'ssh -L'.

The tunnel will die when the ssh's output line (STDIN/STDOUT) match below:

- max\_channel

    Set the max $1 when match /channel (\\d+):/

- grep\_word

    Set the max time when optional word match.

Hold a file lock and generate the tunnel information when output meet 'Entering interactive session'.(The tunnel begin to work)

The file lock will not be released until the tunnel die.

You can use [vayne-tunnel-info](https://metacpan.org/pod/vayne-tunnel-info) to gather all running tunnel info.

# AUTHOR

SiYu Zhao <zuyis@cpan.org>

# COPYRIGHT

Copyright 2016- SiYu Zhao

# LICENSE

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# SEE ALSO
