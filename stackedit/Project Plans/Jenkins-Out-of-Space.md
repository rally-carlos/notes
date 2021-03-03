Address "Controller out of spaces" issues in #jenkins-smes

Vission
* Enable teams to better self serve their Jenkins controller
* Encourge team to optimize/improve builds (via "self serve")
* Reduce support cost/overhead on Jenkins platform owners

Pass 1
* script to query and display builds sorted by size, with links to build
	Maybe crude, but better than nothing and great for first pass
* space alert (slack/email ping) to owner of team controller to address when getting low, (1 GB ? )

Phase 2
* can choose to delete build from cli.

## Notes
* https://gist.github.com/mubbashir/484903fda934aeea9f30#file-remove-dir-in-workspace-groovy
* https://stackoverflow.com/questions/46766294/get-size-of-workspacedirectories-from-jenkinsnodes-via-script
* https://stackoverflow.com/questions/7994379/free-space-in-jenkins-deleting-builds-directory
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc3MjAyOTg5MywxNDQ3NzU0MDVdfQ==
-->