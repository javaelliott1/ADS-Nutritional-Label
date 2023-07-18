![image](https://github.com/javaelliott1/SP22_RDS/assets/89791901/cb597639-ca83-4b2c-84a4-610af060b260)

For Responsible Data Science class

Giving a nutritional label to an automated decision system.

Simulating analyzing a black-box model, we assessed a Kaggle solution to a home credit default risk challenge. This solution was used as a guide to using logistic regression and LGBM models to predict Home Credit Group clients' repayment ability. 

The simplicity of the logistic regression model makes the how-to guide understandable but picks up insigificant signals, and the LGBM model is less understandable to the reader but yields top-tier accuracy. 

Our project is not to question how well the guide works, but whether these models would be harmful if actually applied, and from there asking the question of _should_ this be a guide. We analyzed the solution from a demographic parity and Rawlsian EO perspective.

We were limited in this analysis by the Home Credit team deciding not to publish their true test values, but we focused on age, income, gender, and employment/education/housing types.

We found that the released dataset had:
* Almost twice as many females than males
* Abnormal distribution of income quantiles (Mostly low income or high income)
* Almost everyone were owners of homes/apartments
* Most people were high school/secondary school educated, but there is a decently sized higher-educated group
* Most were working or on pension

Our project used AIF360 to compare mean differences and disparate impact across groups, and used SHAP values for the naive model to show interesting dependence cases to explain our conclusion.

**Summary**
As an ADS that is meant to also be a guide for Kaggle beginners, we want to be forgiving to how little data processing exists and is talked about. But this guide displays a strong lack of fairness to subgroups.

The data provided was inappropriate, skewing towards upper middle class, college educated white women, an innaccurate representation of the population of individuals potentially needing a loan. It also had poor privatization techniques, as any of this information could identify someone given other dataset knowlege, etc.

The ADS bias is high, as it inputted sensitive attributes (our focused subgroups) to both models, despite no bias mitigation techniques. Overall, the more complex LGBM model is risky but accurate, running the risk of bias but yields top tier accuracy, which brings into question Home Credit's own system.

In no way are we comfortable implementing this ADS in the industry, and suggest:
* Adversarial Debiasing for the simple model
* Re-weighing preprocessing and/or threshold optimizer post-processing for the complex model
* Differentially private and representative data collection



