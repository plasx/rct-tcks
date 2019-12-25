

# Setup
installing dependencies:

    brew install python3
    brew install pipenv
    cd rct-tcks
    pipenv install
    
    
    
# Creating tracks via Django Shell
    
    cd app
    python manage.py shell
    
Then in the shell, create a sample track as such:

    from tracks.models import Track
    Track.objects.create(title="Track 1", description="Track 1 Description", url="https://track1.com")