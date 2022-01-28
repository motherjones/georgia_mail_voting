Georgia Mail
================

  - [Overview](#overview)
  - [Methodology](#method)
  - [Limitations](#limitations)
  - [License](#license)

## Overview

This repository contains the code needed to reproduce Mother Jones' analysis of Georgia Secretary of State voting data that shows Georgians are being disenfranchised after the GOP-controlled legislature passed sweeping new restrictions on mail voting last year.

An analysis by the Atlanta Journal-Constitution in November 2021 found that rejected mail ballot applications had quadrupled compared to 2020. But examining rejected applications only tells part of the story. In Georgia, voters can—and many do—file multiple applications for a mail ballot. In some cases, one of those requests may be approved. So Mother Jones zeroed in how many voters never cast a ballot by mail or in person after their mail applications were denied. That yielded a more alarming number: 45 times more Georgians were denied the right to vote in 2021 than in the previous election. Even though mail voting was less crucial before the pandemic, Mother Jones also compared the 2021 election to municipal elections in 2019 and 2017. We found that mail voters last fall were more than 5 times more likely to be disenfranchised than during those previous elections.

<a id="method"></a>

## Methodology

#### How we analyzed Georgia voter data

Mother Jones acquired data for the November general/special elections held in 2021, 2020, 2019 and 2017 from the [Georgia absentee voter file website](https://www.google.com/url?q=https://elections.sos.ga.gov/Elections/voterabsenteefile.do&sa=D&source=docs&ust=1643305036015818&usg=AOvVaw2-rsHnvKU3evc0Pxkw4MLq). Each was filtered to not include “IN PERSON” voting (in person absentee voters in Georgia are early voters), then pivoted into a database of unique voters using their unique voter identification number, counting the total number of applications each voter made and the outcomes of their applications, if they returned their ballot and if their ballot was accepted. We combined [voter history data](https://www.google.com/url?q=https://elections.sos.ga.gov/Elections/voterhistory.do&sa=D&source=docs&ust=1643305125518597&usg=AOvVaw1H8bUPVhccTUeB1oLYHvO-) from the same site, joining each unique voter’s ballot cast.

We were able to identify seven outcomes for mail-in voters across four data points: if an application was approved, if a ballot was returned, if a ballot was rejected, and if a voter cast a vote. In some cases, applications were approved and ballots were returned but no vote was cast (a rejected returned mail-in ballot.) In others, no application was approved or a ballot was not returned but a vote was cast (voter elected to vote in-person instead.)

Voter party association was determined using ballots cast in primaries. Voters do not associate with a political party when they register in Georgia and the state's primaries are open. Mother Jones used ballots cast in 2020 primary elections to associate a voter with a political party. Mother Jones only classified voters as Democrats and Republicans if they voted in just one party primary. Voters who did not cast votes in any primary, cast votes in primaries that had no party affiliation, or cast votes in both Democratic and Republican primaries were not counted.

<a id="limitations"></a>

## Errors and limitations

There are known errors in the absentee voter database that were discovered during cleaning.

There are NAs and "ELECTRONIC" ballot_styles in the database. Mother Jones counted each as mail voting. Electronic voting is a special type of mail voting allowed for certain voters residing overseas who can print their own ballot and mail it to election officials. A review of the 679 ballots with NAs showed that each application has a status_reason that shows it is a rejected mail application or ballot.

There are false positives in the application_status of some entries. Fulton County Voter 12774749's three applications is a good example. All three were submitted on the same day. One was accepted and a ballot was issued. However, the other two applications list the ballot as rejected for duplicates in the status_reason but say they were accepted in the application_status. To calculate the rate of rejection for all applications accurately, Mother Jones changed the application_status of rows where a ballot was listed as rejected in the status reason. The difference was ultimately within a rounding error of AJC's analysis.

<a id="license"></a>

## License

Copyright 2022, Foundation for National Progress

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
