# Running the Notebook

Open [this notebook](https://colab.research.google.com/github/adventHymnals/resources/blob/master/Sheets2Resume.ipynb). Look for the play button to the left of `Show code` under the `Select sheet with cv` section and click on it. Wait for your cv to be compiled. It will take about 7 minutes. Our engineers are working to optimize the code so that it can run faster.

This process will create in your google drive the following directory structure:


```text
.
└── resume_v1
    ├── private
    └── public
        └── resume_v1.xlsx
        └── You_name - Resume.pdf
```

You will be provided with a link to the spreadsheet which will be created for you if you are running this for the first time. Update it with your data and run this process everytime you want your resume (the pdf) to be updated with your data.

>> In case you save resume_v1 as a google sheet, the google sheet will be used instead of the xlsx.

If you have set up github and ssh, then you need to upload the ssh.zip you obtained into `resume_v1/private`. In the sheet called `basic` edit the repo to point to `your-username/vue-resume` and run the code under `Push to Github`. The spreadsheet will be processed and push to github to update your resume there.