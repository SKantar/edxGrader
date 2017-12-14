RAF Open edX Pull Grader
========================

External pull grader for code grading in Open edX courses.
Grader pulled from here:
https://github.com/SKantar/AlgorithmsGrader

Suported languages:
* Python 3.5
* Python 2.7
* C
* C#
* Java
* PHP

Setup
=====
1. Clone repository
2. Update [edx-grader/urls.py](edx-grader/urls.py) with addresses of your XQueue server
3. Update [edx-grader/settings.py](edx-grader/settings.py) with your login information and queue name
4. Run with ```python3 edx_grader.py```

Usage
=====
1. Upload your tester methods in a file through studio file upload tool
2. Create new **Blank Advanced Problem**
3. Edit your **<coderesponse>** XML
4. Add <graader_payload> tag with parameters:
    * lang - Programming language of submitted code
    * num_points - Maximum number of points awarded
    * partial - [True | False] Allow partial points based on the number of tests passed
    * tester - web link to your uploaded file with tester methods

Example problem:
```HTML
<problem>
  <coderesponse queuename="raf_grader">
    <label>Write a program that prints "hello world".</label>
    <textbox rows="10" cols="80" mode="python" tabsize="4" points="10"/>
    <codeparam>
      <initial_display>
        # students please write your program here
        print("")
      </initial_display>
      <answer_display>
        print "hello world"
      </answer_display>
      <grader_payload>
        {
        	"lang": "python3",
        	"num_points": 10,
        	"partial": false,
        	"tester": "<some_address>/asset-v1:RAF+CS101+2016_T1+type@asset+block@hello_world_grader.py"
        }
      </grader_payload>
    </codeparam>
  </coderesponse>
</problem>
```
