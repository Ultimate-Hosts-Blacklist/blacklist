pipeline {
    agent any

    triggers {
        cron('H */4 * * *')
    }

    environment {
        GIT_NAME = credentials('uhb-git-name')
        GIT_EMAIL = credentials('uhb-git-email')
        GITHUB_TOKEN = credentials('uhb-pat')
        GIT_REPO_NAME = env.GIT_URL.replaceFirst(/^.*\/([^\/]+?).git$/, '$1')
    }

    stages {
      stage('Setup miniconda') {
        steps {
          sh script: '''#!/usr/bin/env bash

          set -e

          source ${UHB_CONDA_DIR}/etc/profile.d/conda.sh
          conda create --yes -n ${BUILD_TAG} python=3.9 pip
          ''', label: 'Setup Conda environment'
        }
      }

      stage('Run') {
          steps {
            sh script: '''#!/usr/bin/env bash

            set -e

            source ${UHB_CONDA_DIR}/etc/profile.d/conda.sh

            echo "Activation of the conda environment ..."
            conda activate ${BUILD_TAG}
            echo "Conda environment activated!"

            echo "Let's get the Python version ..."
            python -V
            echo "Got Python version!"

            echo "Let's get the pip version ..."
            pip --version
            echo "Got pip version!"

            echo "Let's install the launcher ..."
            pip install --upgrade ultimate-hosts-blacklist-test-launcher
            echo "Installed launcher!"

            echo "Let's get the PyFunceble version ..."
            PyFunceble --version
            echo "Got PyFunceble version!"

            echo "Let's get the launcher version ..."
            ultimate-hosts-blacklist-test-launcher --version
            echo "Got launcher version!"

            echo "Let's launch the launcher ..."
            ultimate-hosts-blacklist-test-launcher
            echo "Launcher done!"

            echo "Deactivation of the conda environment ..."
            conda deactivate
            echo "Conda environment deactivated!"
            '''
          }
      }
    }

    post {
        always {
            sh script: '''#!/usr/bin/env bash
            source ${UHB_CONDA_DIR}/etc/profile.d/conda.sh

            conda remove --yes -n ${BUILD_TAG} --all
            '''
        }
    }
}
