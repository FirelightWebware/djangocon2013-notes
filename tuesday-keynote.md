# State of the Pony Report

_Speaker: Dr. Russell Keith-Magee_


## The DSF Mission

- Support development of Django
    - sponsored conferences
    - sponsored sprints (paid travel costs of core team developers)
    - grants
        - board has recently formed a formal grants committee, chaired by Lynn Root
    - many corporate members of the DSF
        - (can Firelight be a corporate member? yes - email foundation@djangoproject.com)
- Promote use of Django
    - our community is not good at marketing
    - currently working on a new site for djangoproject.com
    - we need someone who has marketing skills to actively promote Django
    - growing the community
        - [code of conduct](http://djangoproject.com/conduct/)
        - promoting diversity
- Protect IP and long-term viability
    - copyrights
        - Django doesn't own the copyright to Django, it's owned by the community...
          the individuals who have contributed code. if you've contributed code
          you need to sign a formal license thingy.
    - trademarks
        - open source communities need to protect their trademarks
        - the name "django" when applied to software, is a registered trademark
          in the US. the color is part of the trademark.
        - the DSF has developed a trademark licensing agreement, which specifies
          how and when you can use the Django trademark
        - the trademark allows:
            - you to say you are using django
            - use the trademark for open source projects
            - use it to promote community events
            - merchandise (who?)
            - how you can use it in a domain name
        - and you can't:
            - claim you are official
            - can't use the font or color scheme
            - events must have a code of conduct
            - cast django project into disrepute
        - this only applies to the trademark, not nominative use, but there
          are rules around that too
        - if you are incorporating "django" into your own brand, there are yet
          another set of rules
        - [read the rules](http://djangoproject.com/trademarks/)
    - exemptions
        - django has been out for 8 years, and people are using the trademark
          today, but have been using it for longer than the trademark license
          has been around. the DSF can offer these people a custom license.
- Advance the state of the art
    - deliverd 1.5 with python 3 transition and custom user models
    - 1.6 will be out soon
        - formal python 3 transition
        - transaction imporovements
        - persisitent database connections
        - unittest2-compatible test discovery
    - 1.7
        - schema migration!
        - manage.py validation refactor
        - composite foreign key
    - may end up with 2 releases in 12 months, which means 1.4 would be end-of-lifed
      too soon, so there are discussions about Django LTS
    - the future...
        - "real-time" web -- the experience users are expecting to have on the web
          is changing. they expect to see live updates without page refreshes. 
          django needs to support this or it will become obsolete. django needs
          an in-the-box solution. there's no framework that has a stranglehold
          on this yet, so there is still time to solve this before becoming
          obsolete.
        - rich client interfaces -- django has stayed agnostic on the front-end,
          and has been built to be only server-side. but the clean separation between
          server/client doesn't exist any more. if django wants to survive long
          term we need something, not necessarly in-the-box, but a documented
          solution and hooks into django.
    - attracting new users
        - django isn't "cool" any more because it's stable and boring :P
        - we can't ignore what the "cool" kids are doing because they are doing
          useful, if unstable, things
        - make it easier to learn django
        - provide more community resources to newcomers
        - make sure that people who find django stay in the community and their
          first experience is positive and they aren't scared off
    - attracting new developers
        - need to get over the sense that people have that they can't contribute
          because they just aren't good enough
        - most people who go to the trouble of submitting a patch don't submit
          a second one -- this is a wasted opportunity
        - jeremy dunck set up a django core mentorship program, a mailing list
        - need improved dev tools and process
    - funding
        - no core django devs (aside from Andrew on account of the kickstarter)
          are paid to work on Django
        - instead of trying to get one or two big funders, use distributed funding
        - the DSF could range funds from the community to hire someone to work
          full-time on django (not so much coding but project/community management)
            - unknowns: how much money do we need, and who should be hired?
        - is the DSF on gittip? is it possible to donate to a 501c through gittip?



## Reference

