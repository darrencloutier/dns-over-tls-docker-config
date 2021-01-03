# dns-over-tls-docker-config
docker-compose.yml for pihole and dns containers with dns over tls and two upstream providers

# Prerequisites 
- You're running a Raspberry PI with a static IP already assigned.
- Docker and Docker Compose are installed (see <a href="https://dev.to/rohansawant/installing-docker-and-docker-compose-on-the-raspberry-pi-in-5-simple-steps-3mgl" >these great instructions</a> by Rohan Sawant if you need help with this).

# Setup / Testing
- Pull/download docker-compose.yml.
- Uncomment the PiHole WEBPASSWORD line and set your own password.
- Start the containers with this command: docker-compose up -d
- Test the containers by executing the following commands (Look for status: NOERROR):
  - dig github.com @127.0.0.1 -p 5053 (tests that the cloudflare-dns-tls container is resolving)
  - dig github.com @127.0.0.1 -p 50053 (tests that the google-dns-tls container is resolving)
  - dig github.com @127.0.0.1 -p 53 (tests that the PiHole container is resolving)
   - If the dig command is not found, install it: sudo apt-get install dnsutils
- Point your router DNS settings (or individual clients) at the static IP of your Raspberry Pi.
- Browse to your Raspberry Pi IP address in a web browser to utilize the PiHole web UI for stats and other advanced settings.

# Useful Commands
- 'docker-compose stop' to stop your containers.
- 'docker-compose pull' to check for new versions of your containers and update if there are any available.
- 'docker-compose up -d' to start your containers.

