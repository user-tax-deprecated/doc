
apt-get install -y sasl2-bin

configure the saslauthd daemon with MECHANISM="shadow" in /etc/default/saslauthd

/lib/systemd/systemd-sysv-install enable saslauthd

systemctl enable saslauthd --now
