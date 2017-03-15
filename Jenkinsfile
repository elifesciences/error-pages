elifeLibrary {
    def commit
    stage 'Checkout', {
        checkout scm
        commit = elifeGitRevision()
    }

    stage 'Sanity check', {
        sh "composer install --no-interaction"
        sh "bin/update && git diff --exit-code"
    }

    elifeMainlineOnly {
        stage 'Deploy to end2end', {
            // TODO: extract step
            sh "aws s3 cp public s3://end2end-elife-error-pages --recursive"
        }

        stage 'Approval', {
            elifeGitMoveToBranch commit, 'approved'
        }
    }
}
