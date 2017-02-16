# ssh-conf-bosh-release

A release for configuring additional SSH authentication and authorization settings.


## Snippets

    instances:
    - name: jumpbox
      jobs:
      - name: sshd_settings
        release: ssh-conf
        properties:
          disable_authorized_keys: true
          trusted_ca: ((trusted_ca))


### Development

    $ bosh update-cloud-config cloud-config.yml
    $ bosh upload-stemcell bosh-stemcell-3312.15-warden-boshlite-ubuntu-trusty-go_agent.tgz
    $ bosh create-release --force
    $ bosh upload-release
    $ bosh deploy --var-file trusted_ca=test-ca-cert.pub src/bosh-lite/manifest.yml


## License

[MIT License](LICENSE)
