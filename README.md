# PRBot

PRBot is a simple bot that scan for new Issues & Pull Request and Comment on 
it with some special text.

PRBot works purely by scraping the GitHub API on a regular basis. While
[Webhooks](https://developer.github.com/webhooks/) are the "proper" method of
triggering a bot like this one, they also require setup by an organisation or
repository administrator, which isn't always possible.

# Installation

Install dependencies:

    pip3 install -r requirements.txt

Set up configuration in settings.py:

	GITHUB_TOKEN="<Token>"
	PR_FILE="/path/to/pullreq.md"
	ISSUES_FILE="/path/to/issues.md"
	STATUS_FILE="/path/to/status.json"
	REPO_NAME="use/repo"

Add a job to your crontab, e.g.:

	*/5 * * * * /home/username/PRBot/prbot.py 2>&1 | /usr/bin/logger

This example will run the script every 5 minutes and send all output
to syslog.

# Message Format

The message should be in Markdown format for display on the GitHub web
interface.

You can use the placeholder `{{ username }}` to dynamically insert the
GitHub username of the pull request originator:

	Hi @{{ username }},
	
	Thanks for your contribution...

# Copyright

Copyright &copy; 2016-2017 Andrew Donnellan.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or (at
your option) any later version.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
