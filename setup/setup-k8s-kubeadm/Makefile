# Instalação dos pré-requisitos
requirements:
	if [ -x /usr/bin/pacman ]; then \
		xargs -a requirements.txt sudo pacman -Sy --noconfirm; \
	elif [ -x /usr/bin/apt-get ]; then \
		xargs -a requirements.txt sudo apt-get install -y; \
	elif [ -x /usr/bin/yum ]; then \
		xargs -a requirements.txt sudo yum -y install; \
	else \
		echo "No package manager found"; \
	fi