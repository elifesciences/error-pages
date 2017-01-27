elifeLibrary {
    def commit
    stage 'Checkout', {
        checkout scm
        commit = elifeGitRevision()
    }

    stage 'Sanity check', {
        sh "bin/update && git diff --exit-code"
    }

    elifeMainlineOnly {
        stage 'Deploy to end2end', {
            echo "Nothing - yet"
        }

        stage 'Approval', {
            elifeGitMoveToBranch commit, 'approved'
        }
    }
}
