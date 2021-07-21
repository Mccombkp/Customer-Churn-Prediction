# Customer-Churn-Prediction

The data from below is from an AB test on whether a hypothetical, contractual TV company should offer a 7 day premium free trial for 7 days, as opposed to their current 24 hours premium trial. After the end of the trial period, those who have not cancelled, start their billing cycle and pay for the premium.

This company wants to know which policy would result in a higher customer LTV after 6 months. 

The data we have only goes to the beginning of March 2020, so we need to get a little creative on predicting 6 month LTV.

Fortunately, [Peter Fader and Bruce Hardie](http://brucehardie.com/papers/037/BdW_JIM_2018-01-10_rev.pdf) have shown the usefulness of using a Beta Discrete Weibull model to forecast retention.

My analysis is an example of how this model can be implemented using Python.
