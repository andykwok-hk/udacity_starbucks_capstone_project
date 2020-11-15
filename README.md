<h3>Starbucks Capstone Project</h3>
This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks.

This project is to explore the composition of the customer and use their personal information to predict if certain types of promotion is attractive to them.

Blog post: https://medium.com/@andykwokck/starbucks-promotion-ml-project-137139869032

The data is contained in three files:

portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
profile.json - demographic data for each customer
transcript.json - records for transactions, offers received, offers viewed, and offers completed
Here is the schema and explanation of each variable in the files:

portfolio.json

id (string) - offer id
offer_type (string) - type of offer ie BOGO, discount, informational
difficulty (int) - minimum required spend to complete an offer
reward (int) - reward given for completing an offer
duration (int) - time for offer to be open, in days
channels (list of strings)
profile.json

age (int) - age of the customer
became_member_on (int) - date when customer created an app account
gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
id (str) - customer id
income (float) - customer's income
transcript.json

event (str) - record description (ie transaction, offer received, offer viewed, etc.)
person (str) - customer id
time (int) - time in hours since start of test. The data begins at time t=0
value - (dict of strings) - either an offer id or transaction amount depending on the record

<h3>Summary of the result</h3>
From the exploration, we know that male customer is more than female customer which are ~8000 and ~6000 respectively. And most customers' income are around 60000. Median and mean income are 64000 and 65405 respectively. Moreover, we can see that age distribution is quite diversed. With most of the customer clustered around age 50-60. User gradually increased from 2013 and reached the highest at 2017 and dropped in 2018.

Therefore, a model to assist for promotion maybe useful to help retain the customer. The model deployed here are AdaboostClassifier and GaussianNB. We use gender, income, age and year/month that customer become member to see if they are sensitive to bogo/discount promotion. If the ratio of used offer and received offer is equal to or larger than 0.7. We will see them as sensitive to promotion.

If we use the model to predict using the personal information. We will get whether they are sensitive or not to the promotion and choose whether to send out the promotion to them or not. We can also adjust the promotion base on this. If they are not sensitive to promotion. We can send out a more attractive promotion to them e.g. bigger discount in order to retain the customer.

From the result, we can see that GaussianNB is performing better than AdaboostClassifier with the accuracy score 0.797 and 0.833 for bogo and discount promotion respectively. We can also see that identical result (accuracy score) with different parameters. For better performance, other model could be deployed to figure out if there is a better model to boost the accuracy score.

<h3>Author</h3>
Andy Kwok