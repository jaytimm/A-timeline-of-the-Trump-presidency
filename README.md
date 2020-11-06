A timeline of the Trump Presidency
----------------------------------

Time-line scraped from [Wikipedia’s Timeline of the Donald Trump
presidency](https://en.wikipedia.org/wiki/Timeline_of_the_Donald_Trump_presidency),
and made available as a simple function in the
[uspols](https://github.com/jaytimm/uspols) R package – dubbed
`uspols_wiki_timeline()`. As [pdf]().

``` r
library(devtools)
devtools::install_github("jaytimm/uspols")
library(uspols) 
```

``` r
longs <- uspols::uspols_wiki_timeline()
```

``` r
library(tidyverse)
## Some cleaning for web/pdf
longs$Events <- gsub('&', '+', longs$Events)
longs$Events <- gsub('\\$', '', longs$Events)
longs$Events <- stringi::stri_trans_general(longs$Events, 
                                            "latin-ascii")

longs2 <- longs %>% 
  filter(!is.na(Events)) %>%
  mutate(daypres = as.integer(daypres)) %>%
  group_by(daypres, date) %>%
  arrange(daypres) %>%
  summarize(Events = paste0(Events, 
                            collapse = ' | ')) %>%
  ungroup() %>%
  mutate(Events = paste0('**', 
                         daypres, ' | ', 
                         date, '**: ', 
                         Events))

l1 <- paste0(longs2$Events, 
             collapse = ' || ')  # `r l1` inline 
```

### A maelstrom in one fell swoop

**1 \| 2017-01-20**: 45th President Donald Trump and 48th Vice President
Mike Pence take the Oath of Office. \| President Trump proclaims a
National Day of Patriotic Devotion. \| According to contested reports in
December 2017, while seated at Trump’s inauguration speech, forthcoming
National Security Advisor Michael Flynn texts a former business partner
that Russian sanctions blocking a private Russian-backed plan to build
nuclear plants in the Middle East will now be ‘ripped up’. \| State
officials in Florida, Delaware and New York confirm that they have not
received paperwork that the President has relinquished control over his
companies despite earlier promises to do so. \| President Trump issues
Executive Order 13765 to scale back parts of the Affordable Care Act. \|
The Trump administration suspends an Obama administration cut to Federal
Housing Authority mortgage insurance premiums. \| President Trump signs
a bill waiving a rule that requires military personnel to wait seven
years after retiring before serving in a civilian post, to allow retired
Marine general James Mattis to become U.S. Secretary of Defense. The
Senate confirms Jim Mattis as the 26th U.S. Secretary of Defense in a
vote of 98-1 and retired Marine general John F. Kelly as the 5th U.S.
Secretary of Homeland Security in a vote of 88-11. \| Protests damage
parts of downtown Washington, D.C. and lead to 217 arrests and 9
injuries. \|\| **2 \| 2017-01-21**: Four million people around the world
attend the Women’s March protesting the new administration. It was the
largest single-day protest in U.S. history. \| President Trump and Vice
President Pence speak at the CIA headquarters. \| White House Press
Secretary Sean Spicer accuses the media of inaccurately representing the
presidential inauguration attendance. Spicer does not take questions
from the press and is criticized for making inaccurate statements. \|
President Trump appoints Michael Flynn as National Security Advisor. \|
Two U.S. drone strikes in Yemen’s Al Bayda Governorate are the first
reported drone actions under the Trump administration. \| Possible
secure video call to discuss sanctions again the FSB and GRU between
Donald Trump and Vladimir Putin, suggested by Sergey Kislyak to Michael
Flynn during a December 29th, 2016 phone call. \|\| **3 \| 2017-01-22**:
President Trump calls Israeli Prime Minister Benjamin Netanyahu to
discuss Iran, ISIS, and the Israeli-Palestinian peace process. \| Vice
President Pence administers the oath of office for the White House
senior staff. \| White House counsellor Kellyanne Conway coins the term
‘alternative facts’ during an interview. \| White House announces that
they will not release President Trump’s tax returns. \| President Trump
speaks to Governor of Georgia Nathan Deal about the tornado outbreak in
the Southeast which killed 20 people and caused 1.3 billion in damage.
\| Foreign advisor George Papadopoulos meets in Washington D.C. with the
head of Israel’s Shomron Regional Council, Yossi Dagan. \|\| **4 \|
2017-01-23**: President Trump meets with twelve CEOs of major U.S.
companies. \| President Trump signs three memoranda. The first withdraws
the United States from the Trans-Pacific Partnership. Another reinstates
the Mexico City Policy, which bars international NGOs from receiving
foreign aid that “offer or promote abortions as part of their family
planning services”. The third initiates a 90-day hiring freeze on the
federal workforce. \| President Trump claims that 3-5 million illegal
votes cost him the popular vote in a private meeting with congressional
leaders. \| President Trump speaks with Egyptian President Abdel Fattah
el-Sisi, saying that the United States remains committed to their
relationship and to continue military assistance to Egypt, discussing
ways the United States could support Egypt’s economic reform program. \|
The Senate confirms Mike Pompeo as the Director of the CIA in a vote of
66-32. \| A federal-court lawsuit is filed accusing President Trump of
violating the Constitution’s Foreign Emoluments Clause. \| President
Trump elevates Ajit Varadaraj Pai as chairman of the Federal
Communications Commission. \| The Trump administration removed from the
United States Department of State’s website the former United States
Secretary of State John Kerry’s apology for the Lavender Scare. \|\| **5
\| 2017-01-24**: President Trump signs Executive Order 13766, which
expedites environmental reviews and approvals for future infrastructure
projects. \| President Trump signs four memoranda. Two of them reverse
the Obama administration’s halt on the Keystone XL and Dakota Access oil
pipelines, the latter of which has been the subject of protests by the
Standing Rock tribe. President Trump says these projects will recover
28,000 jobs. Another memorandum requires that the pipelines use domestic
steel (a directive shortly overturned by the White House in respect of
Keystone), and the last calls for “expedited reviews of and approvals
for” manufacturing facilities and “reductions in regulatory burdens”
affecting domestic manufacturing. \| President Trump speaks with Indian
Prime Minister Narendra Modi. \| Michael Flynn is interviewed by the FBI
about prior conversations with Russian Ambassador Sergey Kislyak. Flynn
pleads guilty on December 1, 2017, to lying during the interview. \| The
Senate confirms Nikki Haley as the Ambassador to the United Nations in a
vote of 96-4. \|\| **6 \| 2017-01-25**: President Trump issues Executive
Order 13767 directing the Department of Homeland Security to begin
construction of a wall on the Mexico-United States border. Mexican
President Enrique Pena Nieto rejects the idea that Mexico would pay for
any border wall between the United States and his country. \| President
Trump issues Executive Order 13768 cutting federal funding for sanctuary
cities who refuse to comply with immigration enforcement measures. The
order also increases border patrol and immigration officers and changes
deportation standards. \| President Trump bans United States
Environmental Protection Agency employees from contact with journalists
or engagement on social media. \| President Trump announces that he
intends to investigate alleged voter fraud from the 2016 presidential
election. \|\| **7 \| 2017-01-26**: President Trump visits Philadelphia
to address Congressional Republican leaders, regarding his agenda. He
speaks at the Loews Hotel, along with British Prime Minister Theresa
May. \| Press Secretary Sean Spicer announces that the border wall might
be funded by a 20% tax on imports from Mexico. \| Mexican President
Enrique Pena Nieto cancels a proposed meeting with Trump due to the
controversy where Trump suggested Mexico pay fully for the wall. \|
President Trump proclaims the start of National School Choice Week. \|
Patrick F. Kennedy, Joyce Anne Barr, Michele Thoren Bond and Gentry O.
Smith resign from the Department of State, after Victoria Nuland and
Gregory B. Starr decline to stay on in the Trump administration. \|
Acting Attorney General Sally Yates informs White House Counsel Don
McGahn that National Security Advisor Michael Flynn’s public account of
his interactions with Russian officials during the transition were
untruthful, making him vulnerable to blackmail. \|\| **8 \|
2017-01-27**: President Trump speaks with Mexican President Enrique Pena
Nieto on the phone to discuss Mexico-United States relations in lieu of
their canceled meeting. \| President Trump holds a bilateral meeting and
joint press conference with British Prime Minister Theresa May at the
White House, where they discuss sanctions on Russia, NATO, U.S. torture
policy. May is the first foreign leader to visit Trump since his
inauguration. \| During a visit to the Pentagon, President Trump signs
Executive Order 13769, suspending the Refugee Admissions Program for 120
days and denying entry to citizens of Iraq, Iran, Libya, Somalia, Sudan,
Syria, and Yemen for 90 days. \| President Trump signs a memorandum
calling for budget negotiations about the expansion and strengthening of
the U.S. military. \| Vice President Pence speaks at the March for Life
in Washington D.C. \| President Trump has a one-on-one dinner with FBI
Directory James Comey. Later news reports state that Trump asks Comey to
pledge loyalty to Trump, and Comey demurs. The White House denies this
version of events. \| Trump advisor George Papadopoulos is interviewed
by the FBI concerning Russian meetings in 2016. He pleads guilty in
October 2017 to making omissions and false statements during the
interview. \|\| **9 \| 2017-01-28**: President Trump speaks on the phone
with Russian President Vladimir Putin, German Chancellor Angela Merkel,
Japanese Prime Minister Shinzo Abe, Australian Prime Minister Malcolm
Turnbull, and French President Francois Hollande. \| President Trump
signs Executive Order 13770, which enacts a five-year ban on lobbying
for presidential appointees after leaving the White House. He also
enacts a lifetime ban for officials lobbying on behalf of a foreign
government and directs his generals to put together a plan within 30
days for Defeating ISIS. \| Executive Order 13769 goes into effect. Iran
says it will take reciprocal action against the United States. U.S.
District Judge Ann Donnelly in New York grants a stay of the executive
order that allows people with valid visas who landed in the U.S. to
temporarily remain in the country. \| President Trump signs a memorandum
to create a plan within 30 days to defeat ISIS, and another to
restructure the National and Homeland Security Councils by downgrading
the Chiefs of Staff and appointing the Assistant to the President and
Chief Strategist Steve Bannon. \|\| **10 \| 2017-01-29**: President
Trump speaks with Saudi Arabia’s King Salman and acting South Korean
President Hwang Kyo-ahn. \| The Yakla raid, the first commando raid
authorized by President Trump, leads to the death of Chief petty officer
William Owens, 14 members of the Al-Qaeda in the Arabian Peninsula as
reported by the United States government, and 14-25 Yemeni or other
nationality civilian casualties, including American Nawar “Nora”
al-Awlaki. \| Federal judges in the states of Massachusetts, Virginia,
and Washington sign orders halting implementation of parts of Executive
Order 13769. Chief of Staff Priebus states that people from the affected
countries who have a green card, will not be prevented from returning to
the United States. \|\| **11 \| 2017-01-30**: President Trump signs
Executive Order 13771, which seeks to reduce the number of federal
regulations by requiring agencies to repeal two existing regulations for
every new rule introduced. \| President Trump fires acting Attorney
General Sally Yates after she ordered employees of the Department of
Justice not to enforce the President’s ban due to doubts over its
legality. Dana Boente takes her place as acting Attorney General. That
same night, Trump replaces Daniel H. Ragsdale with Thomas D. Homan as
acting director of U.S. Immigration and Customs Enforcement (ICE). \|
President Trump announces he will continue to enforce Executive Order
13672, signed by former President Obama in 2014 that established legal
protections for LGBT workers. \| A petition, launched Sunday to cancel
President Trump’s state visit to the United Kingdom in October, tops 1
million signatures, passing the threshold for British Parliament debate,
eventually reaching 1.8 million. A British government spokesman says the
state visit would still go ahead as planned. \| The Iraqi Parliament
votes in favor of a reciprocal travel ban on American citizens if
President Trump’s executive order barring citizens of Iraq and six other
Muslim-majority countries is not reversed. The Iraqi travel ban will not
be implemented while tens of thousands of U.S. soldiers and contractors
are involved in the fight against ISIL. \|\| **12 \| 2017-01-31**:
President Trump nominates Neil Gorsuch as an Associate Justice of the
Supreme Court to fill the vacancy left by Antonin Scalia, who died in
February 2016. \| The Senate confirms Elaine Chao as the 18th U.S.
Secretary of Transportation in a vote of 93-6. \|\| **13 \|
2017-02-01**: President Trump visits Dover Air Force Base for the
arrival of the remains of Navy SEAL Chief Special Warfare Operator
William Owens who had been killed in action in Yemen three days prior,
the first known combat death under the Trump administration. \| The
Senate confirms Rex Tillerson as the 69th U.S. Secretary of State in a
vote of 56-43. \| President Trump discusses a refugee agreement in a
truncated phone call with Australian Prime Minister Malcolm Turnbull,
describing it to Turnbull as a ‘disgusting deal’. \| President Trump
proclaims February as National African American History Month. \| The
Mercury Effluent Rule which governed the use and disposal of mercury at
dental offices is withdrawn by the administration. \| White House
advisor Jared Kushner meets with China’s Ambassador to the U.S., Cui
Tiankai. \|\| **14 \| 2017-02-02**: President Trump speaks at the
National Prayer Breakfast and holds a bilateral meeting with King
Abdullah II of Jordan. He also promises to dismantle the Johnson
Amendment prohibiting religious organisations from giving political
donations while maintaining a tax-free status. \| President Trump
proclaims February as American Heart Month. \| President Trump warns
Israel that building new settlements in the West Bank “may not be
helpful” for a peace deal. \| The Department of the Treasury eases some
sanctions on the Federal Security Service, allowing for limited
transactions with the intelligence agency. \| Secretary of State
Tillerson meets German Foreign Minister Sigmar Gabriel. \| Ambassador to
the United Nations Nikki Haley declares to the United Nations Security
Council that sanctions against Russia for its Crimean conflict would not
be lifted until Russia returned control over the region to Ukraine. \|
Then-Uber CEO Travis Kalanick resigns from the president’s business
advisory council, citing a concern that his participation would be seen
as an endorsement of Trump. \|\| **15 \| 2017-02-03**: President Trump
signs Executive Order 13772, which instates a review of the Dodd-Frank
Act. \| President Trump signs a memorandum directing the Department of
Labor to review a fiduciary rule signed during the Obama administration
before its implementation in April. \| President Trump institutes
economic sanctions on 13 Iranian individuals and 12 companies from the
nation after a recent ballistic missile test. \| Senior federal judge
James Robart of the District Court for the Western District of
Washington temporarily blocks President Trump’s order to temporarily
block immigration from seven middle-eastern nations. \| Secretary of
State Tillerson meets with Jordanian Minister of Foreign Affairs Ayman
Al Safadi, as well as United Nations and Arab League Envoy to Syria
Staffan de Mistura. \| Trump-appointed Federal Communications Commission
chairman revokes an agreement with internet service providers for
cheaper internet for poor communities. \| Vincent Viola withdraws his
name from consideration as Secretary of the Army. \| The Department of
the Treasury launches sanctions against supporters of Iran’s ballistic
missile program. \|\| **16 \| 2017-02-04**: President Trump’s official
Facebook page makes a false claim about Kuwait instating a travel ban
similar to Executive Order 13769, while the Department of Justice
appeals a court decision to overturn the executive order. The President
criticizes James Robart for making the decision, referring to him as a
“so-called judge”. \| President Trump speaks with Italian Prime Minister
Paolo Gentiloni, confirming his attendance to the 2017 G7 summit in
Sicily, and with Ukrainian President Petro Poroshenko about the ongoing
Ukrainian crisis. \|\| **17 \| 2017-02-05**: The Ninth Circuit Court of
Appeals denies a request from the Trump Administration to immediately
reinstate the temporarily blocked travel ban. \| President Trump speaks
with NATO Secretary General Jens Stoltenberg and New Zealand Prime
Minister Bill English. \|\| **18 \| 2017-02-06**: President Trump
addresses troops at the MacDill Air Force Base and the Central Command.
\| The Department of Justice asks the Ninth Circuit Court of Appeals to
restore the temporarily blocked immigration ban. \|\| **19 \|
2017-02-07**: The Senate confirms Betsy DeVos as the 11th U.S. Secretary
of Education by a vote of 51-50. As president of the Senate, Vice
President Mike Pence is the first vice president since 1945, to cast a
tie-breaking vote to confirm a Cabinet member. \| The President falsely
claims that the murder-rate in America is at a 47-year-high. \| The
House Committee on House Administration led by the President’s party
votes to eliminate the Election Assistance Commission, the only federal
agency tasked with preventing the hacking of voting machines. \|
President Trump speaks with Spanish Prime Minister Mariano Rajoy and
Turkish President Recep Tayyip Erdogan, confirming his support of NATO
and discussing joint action against ISIS. \| The President tells a
sheriff they should destroy the career of a Texas state law-maker who
opposed civil forfeiture. \|\| **20 \| 2017-02-08**: The Senate confirms
Jeff Sessions as the 84th U.S. Attorney General in a vote of 52-47. \|
President Trump formally announces his full Cabinet, comprising 24
members. The position of Chairman of the Council of Economic Advisers is
removed and the Director of National Intelligence and Director of the
CIA are elevated to cabinet-level. \| President Trump writes a brief
letter to Chinese President Xi Jinping. \| The President publicly
chastises Nordstrom for not carrying his daughter Ivanka Trump’s brand.
\| Secretary of State Tillerson meets with Canadian Minister of Foreign
Affairs Chrystia Freeland. \|\| **21 \| 2017-02-09**: Jeff Sessions is
sworn in as the 84th U.S. Attorney General. \| The President refers to
Elizabeth Warren as ‘Pocahontas’ due to her claimed Native American
ancestry. \| President Trump signs Executive Order 13775, which changes
the line of succession for the Department of Justice. \| President Trump
signs three executive orders regarding law enforcement: Executive Order
13773, 13774 and 13776. \| The Ninth U.S. Circuit Court of Appeals
denies the Trump administration’s appeal to block the lower-court ruling
that halted the travel ban. \| President Trump agrees to continue the
One China Policy after a discussion with Chinese President Xi Jinping.
\| Secretary of State Tillerson meets with European Union High
Representative Federica Mogherini. \|\| **22 \| 2017-02-10**: President
Trump holds a bilateral meeting and joint press conference with Japanese
Prime Minister Shinzo Abe at the White House. The two leaders travel to
Mar-a-Lago in Palm Beach, Florida. \| The Senate confirms Tom Price as
the 23rd U.S. Secretary of Health and Human Services in a vote of 52-47.
\| Secretary of State Tillerson meets with Japanese Minister of Foreign
Affairs Fumio Kishida, and Georgian Minister of Foreign Affairs Mikheil
Janelidze. \| Aboard Air Force One, President Trump tells reporters he
is considering issuing a revised policy banning citizens of certain
countries traveling to the United States. \|\| **23 \| 2017-02-11**:
President Trump and Japanese Prime Minister Shinzo Abe play golf
together at the Trump National Golf Club in Jupiter, Florida and
reportedly discuss the “future of the world, future of the region, and
future of Japan and the United States,” as well as a North Korean
Pukkuksong-2 missile which was test-launched during the meeting. \|
President Trump claims without evidence that three million votes were
cast illegally for Hillary Clinton in the 2016 election which he won.
\|\| **24 \| 2017-02-12**: Stephen Miller, a White House advisor,
repeats the claim of illegal voting on a television interview. \| The
President and Shinzo Abe hold talks at Mar-a-Lago over North Korea while
regular diners are present. \|\| **25 \| 2017-02-13**: President Trump
holds a bilateral meeting and joint press conference with Canadian Prime
Minister Justin Trudeau at the White House. \| Michael Flynn resigns as
National Security Advisor, following alleged discussions with Russian
ambassador Sergey Kislyak regarding the U.S. sanctions on Russia. Keith
Kellogg becomes acting National Security Advisor. \| The Senate confirms
Steve Mnuchin as the 77th U.S. Secretary of the Treasury in a vote of
53-47 and unanimously confirms David Shulkin as the 9th U.S. Secretary
of Veterans Affairs. Shulkin is the first non-veteran to serve as the
U.S. Secretary of Veterans Affairs. \| The Department of the Treasury
sanctions Tareck El Aissami, Vice President of Venezuela. \|\| **26 \|
2017-02-14**: FBI Director James Comey and other officials give
President Trump a briefing on counter-terrorism in the Oval Office.
According to a statement Comey would later make to the Senate
Intelligence Committee, after the briefing, Trump speaks to Comey
one-on-one about the FBI investigation of Mike Flynn, saying “I hope you
can let this go”. \| The Senate confirms Linda McMahon as Administrator
of the Small Business Administration. \| President Trump discusses the
opioid epidemic with Governor of New Jersey Chris Christie. \| Secretary
of State Tillerson meets with Israeli Prime Minister Benjamin Netanyahu
and Qatari Foreign Minister Mohammed bin Abdulrahman Al Thani. Under
Secretary of State Shannon meets Russian and Norwegian Ambassadors to
the U.S. Sergey Ivanovich Kislyak and Kare R. Aas. \| President Trump
signs H.J.Res.41 into law, which nullifies a federal law requiring
resource extraction issuers to disclose payments made for “commercial
development of oil, natural gas, or minerals”, or with foreign and
domestic governments. Trump is the first president in sixteen years to
sign a Congressional Review Act disapproval resolution. \|\| **27 \|
2017-02-15**: President Trump holds a bilateral meeting and joint press
conference with Israeli Prime Minister Benjamin Netanyahu at the White
House. Trump calls on Netanyahu to “hold back” the construction of
settlements in the West Bank. \| President Trump’s comments on the
Israeli-Palestinian conflict prompts Secretary-General of the United
Nations Antonio Guterres to warn against any abandonment of the
two-state solution. \| Andrew Puzder withdraws his nomination to be
Secretary of Labor. \| Chief of Staff Priebus asks Deputy Director of
the FBI Andrew G. McCabe to publicly dispute reports that associates of
President Trump had been in regular communication with Russian agents,
and is rebuffed. \| Under Secretary of State Shannon meets with
Indonesian Ambassador to the U.S. Budi Bowoleksono. \| Secretary of the
Treasury Mnuchin appoints Eli Miller as Treasury Chief of Staff. \|\|
**28 \| 2017-02-16**: Alexander Acosta is nominated to be Secretary of
Labor, and Mick Mulvaney is sworn in as the director of the Office of
Management and Budget in a vote of 51-49. \| President Trump holds a
press conference, defending his administration, criticizing “dishonest”
press coverage thereof, denying Russian connections, and questioning
Hillary Clinton’s conduct towards Russia. \| Robert Harward, a former
Vice Admiral, declines President Trump’s offer to replace Mike Flynn as
National Security Advisor. \| President Trump signs legislation
nullifying the Stream Protection Rule, a midnight regulation by the
Obama administration regulating coal mining. \| The United States
Department of Agriculture is instructed to replace the term ‘climate
change’ with ‘weather extremes’ and ‘reduce greenhouse gases’ with
‘build soil organic matter, increase nutrient use efficiency’ and noting
to staff that climate change should no longer be a priority. \|
Secretary of State Tillerson meets with foreign ministers of G20
countries in Bonn, Germany. \| Secretary of Defense Mattis says that the
United States is not currently prepared to collaborate with Russia on
military matters, including future anti-ISIL U.S. operations. \| George
Papadopoulos is interviewed for a second time by the FBI. In the
following days, he deletes his Facebook account which he had run since
2005 (containing correspondence concerning Russia), opens a new Facebook
account and changes his telephone number. \| Day Without Immigrants 2017
protests are held throughout the United States to demonstrate the
importance of immigration. \|\| **29 \| 2017-02-17**: President Trump
visits Boeing’s North Charleston, South Carolina assembly facility for
the unveiling of its new 787-10 Dreamliner aircraft. He emphasizes his
administration’s commitment to improve the business climate and help
create American jobs. \| From Mar-a-Lago President Trump describes on
Twitter a wide range of mainstream news organizations as “the enemy of
the American people”. \| Scott Pruitt is approved by the U.S. Senate as
the 14th Administrator of the Environmental Protection Agency in a vote
of 52-46. \| Secretary of State Tillerson attends a meeting on the
Syrian Civil War and meets with foreign ministers from three more
countries during his trip to Bonn, Germany. \|\| **30 \| 2017-02-18**:
President Trump holds a rally in Melbourne, Florida, attended by an
estimated 9,000 supporters, where he defends his actions and criticizes
the media. \| Vice President Pence speaks at the Munich Security
Conference in Germany, touching upon the issues of terrorism and defense
spending. \|\| **31 \| 2017-02-19**: The Trump administration asks the
Council of Economic Advisers to predict 3.5% annual GDP growth, while
the Federal Reserve had predicted 1.8%, just over half that. \|\| **32
\| 2017-02-20**: Lieutenant general H. R. McMaster is appointed the 26th
National Security Advisor. Keith Kellogg, who had been the acting
National Security Advisor, remains as the National Security Council’s
Chief of Staff \| Not My Presidents Day protests against the presidency
across the country. \| The Bureau of Land Management is instructed to
lift a moratorium on new coal mine leases on federal land, which have
40% of existing mines. \|\| **33 \| 2017-02-21**: President Trump visits
the National Museum of African American History and Culture and
addresses the increase in vandalism and bomb threats at Jewish community
centers around the country. \| The Trump administration announces the
creation of 15,000 new positions in immigration enforcement, with the
intention of deporting illegal immigrants. The Trump administration
releases a memo that sets the policy for the deportation of undocumented
migrants accused of any crime. \|\| **34 \| 2017-02-22**: The Trump
International Hotel in Washington D.C. received 40-60,000 dollars from
an event paid for by the Embassy of Kuwait, which has been argued to
break the Emoluments Clause because the President has not divested from
his companies. \| The Trump administration rescinds a bathroom policy
for transgender students that had been instated by the Obama
administration. \| Secretary of State Tillerson meets with Australian
minister for Foreign Affairs Julie Bishop. \| Secretary of State
Tillerson and Secretary of Homeland Security Kelly arrive in Mexico for
bilateral talks with the government of President Enrique Pena Nieto.
\|\| **35 \| 2017-02-23**: President Trump meets with 24 manufacturing
CEOs at the White House. \| It is confirmed that six White House staff
members, including Chief Digital Officer Gerrit Lansing, were removed
from their positions earlier in the month after failing FBI background
checks. \| Press Secretary Spicer tells reporters that the
administration plans on increasing enforcement of the Controlled
Substances Act against recreational cannabis use. \| Attorney General
Sessions rescinds a memorandum signed by former President Obama meant to
phase out private federal U.S. prisons. \| Secretary of State Tillerson
and Secretary of Homeland Security Kelly meet Mexican Interior Secretary
Miguel Angel Osorio Chong. \| The Department of the Treasury sanctions
Al-Nusra Front leaders. \|\| **36 \| 2017-02-24**: President Trump holds
a bilateral meeting with Peruvian President Pedro Pablo Kuczynski at the
White House. \| President Trump gives a speech in Oxon Hill, Maryland to
the 2017 Conservative Political Action Conference. In the speech, he
addresses numerous themes including immigration, ISIS and coal mining,
and media reliability, suggesting limits on the use of anonymous sources
by news agencies. \| The New York Times is barred from the White House
press briefing along with the BBC, CNN, Politico, The Huffington Post,
The Los Angeles Times and BuzzFeed News, prompting criticism from the
White House Correspondents’ Association. \| President Trump signs
Executive Order 13777, requiring all federal agencies to create task
forces to determine which regulations hurt the U.S. economy. \|
Secretary of State Tillerson meets with Iraqi National Intelligence
Service Chief Mustafa Kadhimi. \|\| **37 \| 2017-02-25**: President
Trump discusses the Affordable Care Act and the states’ role in
healthcare with Governor of Wisconsin Scott Walker and Governor of
Florida Rick Scott. \| President Trump becomes the first sitting
president to skip the White House Correspondents’ Dinner since 1981,
when Ronald Reagan was recovering from an assassination attempt. \|\|
**38 \| 2017-02-26**: Philip M. Bilden withdraws from his nomination for
Secretary of the Navy. \| President Trump attends the National Governors
Association dinner. \|\| **39 \| 2017-02-27**: President Trump proposes
a 10% increase in military spending of 54 billion diverted from numerous
other budgets, including that of the State Department and the
Environmental Protection Agency. Congress receives a letter criticizing
this plan, signed by more than 120 retired U.S. admirals and generals,
including a former Army Chief of Staff George W. Casey Jr. \| The United
States Department of Justice drops a six-year lawsuit alleging that the
Texas Voter ID law is racist. \| The Senate confirms Wilbur Ross as the
39th U.S. Secretary of Commerce by a Senate vote of 72-27. \| Former
President George W. Bush offers implicit criticism of the Trump
administration’s handling the free press and religious freedom on the
TODAY show. \| Secretary of State Tillerson meets with Egyptian Foreign
Minister Sameh Shoukry. \|\| **40 \| 2017-02-28**: Wilbur Ross is sworn
in as the 39th U.S. Secretary of Commerce. \| Ahead of his Congress
speech, President Trump meets privately with national news anchors,
signaling his willingness to enact an immigration reform bill that could
grant legal status to millions of undocumented immigrants. \| President
Trump delivers his first address before a joint session of the members
of Congress, addressing a wide range of matters including drug abuse,
gang crime, immigration, terrorism, the Mexico-United States barrier,
infrastructure, foreign trade and the stock market. \| President Trump
signs Executive Orders 13778 and 13779. The first initiates a review of
the Clean Water Rule, and the second is meant to “Promote Excellence and
Innovation at Historically Black Colleges and Universities”. \|
President Trump signs a bill removing restrictions on the purchase of
guns by persons with mental illnesses. \| Secretary of State Tillerson
meets with Chinese State Councilor Yang Jiechi. \| To stop leaks, the
White House approves a rule allowing the staff’s cell phones to be
searched. \|\| **41 \| 2017-03-01**: The Senate confirms Ryan Zinke as
the 52nd U.S. Secretary of the Interior by a vote of 68-31. \| The House
Intelligence Committee opens an inquiry into allegations of Russian
interference in the 2016 United States elections. \| The Department of
Justice confirms that Attorney General Sessions met Russian Ambassador
Sergey Kislyak two times in 2016. \| President Trump proclaims March as
the month of Women’s History, Irish-American Heritage, and the American
Red Cross. \| Secretary of State Tillerson meets with Norwegian Minister
of Foreign Affairs Borge Brende. \| President Trump releases his 2017
Trade Policy Agenda. \|\| **42 \| 2017-03-02**: President Trump tells
reporters that he has “total” confidence in Attorney General Jeff
Sessions, then delivers a speech aboard the aircraft carrier USS Gerald
R. Ford (CVN-78), reiterating his commitment to increase military
spending. \| Attorney General Jeff Sessions recuses himself from any
inquiries involving allegations of Russian interference in the 2016
American election. \| The Senate confirms Ben Carson as the 17th U.S.
Secretary of Housing and Urban Development by a vote of 58-41 and Rick
Perry as the 14th U.S. Secretary of Energy by a vote of 62-37. \| The
White House verifies that Jared Kushner met with Sergey Kislyak
alongside Michael T. Flynn at New York City’s Trump Tower in December
2016. \| Secretary of State Tillerson meets with Director General of the
International Atomic Energy Agency Yukiya Amano. \| On his first day,
Secretary of the Interior Ryan Zinke signs two secretarial orders
reducing regulations on hunting and angling on public lands. \| The
Environmental Protection Agency withdraws its request for information on
equipment and emissions at existing operations for the oil and gas
industry in response to H.J.Res.41. \|\| **43 \| 2017-03-03**: The White
House hires three former lobbyists in agencies they had lobbied against,
in violation of President Trump’s own ethics rules. \| An ethics course
for new White House staff is eliminated. \| It is revealed that a
personal email Vice President Mike Pence had used as Governor of Indiana
was hacked. \| \| President Trump and Secretary of Education Betsy DeVos
visit Saint Andrew Catholic School in Orlando, Florida. \| President
Trump attends a Republican fundraising event at the Four Seasons hotel
in Palm Beach, Florida. \| Secretary of State Rex Tillerson meets with
Indian Foreign Secretary Subrahmanyam Jaishankar. \|\| **44 \|
2017-03-04**: In a series of tweets, President Trump publicly accuses
former President Obama of intercepting communications at his offices in
New York City’s Trump Tower in October 2016; Obama spokesman Kevin Lewis
denies the claim. \| The White House proposes to cut the budget of the
National Oceanic and Atmospheric Administration by 17 percent. \| The
President squabbles with Arnold Schwarzenegger on Twitter over the
ratings of The Apprentice, which both have hosted. \| March 4 Trump
rallies are held throughout the United States in support of President
Trump. \| Mexico opens legal aid centers in its 50 U.S. consulates to
defend its citizens’ rights amid the United States “crackdown” on
illegal immigration.Public Safety Minister Ralph Goodale says Canada
will not tighten its border because more migrants, reacting to the
United States immigration crackdown, are illegally crossing into Canada
from the U.S. \|\| **45 \| 2017-03-05**: James R. Clapper, a former
Director of National Intelligence, denies the wiretapping claims of
President Trump’s election campaign and states that the agencies he
supervised found “no evidence of collusion” between the Trump campaign
and Russian officials. \| Congressman Devin Nunes (R-CA), chairman of
the House Intelligence Committee, agrees to a demand from the White
House for an investigation into abuses of executive power by former
President Obama. \|\| **46 \| 2017-03-06**: President Trump signs
Executive Order 13780, seen as a revised version of Executive Order
13769, effective March 16, removing Iraq from affected countries and
clarifying that lawful permanent residents are excluded from the travel
ban. Trump also signs a memorandum to increase immigration law
enforcement. \| President Trump proclaims March 5 as the start of
National Consumer Protection Week. \|\| **47 \| 2017-03-07**: President
Trump speaks on the telephone with Prime Minister Shinzo Abe to voice
his support for Japan in reaction to new reports of North Korean missile
tests. \| President Trump supports a bill that would repeal the
Affordable Care Act and leave 21 million without health insurance
according to the Congressional Budget Office. \| The White House
verifies that President Trump has not conferred with the FBI over
allegations of wiretapping by the previous administration. \| Secretary
of State Tillerson meets with Ukrainian Foreign Minister Pavlo Klimkin.
\|\| **48 \| 2017-03-08**: Formal drafting of the repeal of the
Affordable Care Act begins. \| Federal judge Derrick Watson permits
Attorney General of Hawaii Doug Chin to submit a lawsuit against
President Trump’s newly revised travel ban, to be heard on March 15. \|
President Trump discusses reducing prescription drug prices with
democratic congressmen at the White House. \| The Committee on Oversight
and Government Reform writes to the White House with concern that
President Trump’s deletion of social media postings may constitute a
violation of the Presidential Records Act. \| President Trump discusses
immigration with Laurene Powell Jobs. \| Secretary of State Tillerson
meets with Israeli Minister of Defense Avigdor Lieberman. \| Day Without
a Woman strikes occur on International Women’s Day in protest of the
Trump administration. \|\| **49 \| 2017-03-09**: President Trump pledges
to remove certain regulations pertaining to the Dodd-Frank Wall Street
Reform and Consumer Protection Act at a White House meeting with
community bankers. \| Trump-appointed EPA administrator Scott Pruitt
says he does not believe that carbon dioxide was a primary contributor
to global warming. \| The states of Washington, New York, Oregon and
Massachusetts join Minnesota and Hawaii’s legal challenge to President
Trump’s forthcoming travel ban. \| Office of Government Ethics demands
reprimands for Kellyanne Conway for advertising Ivanka Trump’s products
on television, but the White House refuses. \| In an interview with Fox
News, Vice President Pence states that he learns from the day’s news
reports that Michael Flynn was acting as an unregistered foreign agent
of the Turkish government during the campaign. \|\| **50 \|
2017-03-10**: President Trump speaks by telephone with Palestinian
President Mahmoud Abbas, extending a personal invitation to the White
House. \| President Trump and Attorney General Sessions order the
resignation of 46 U.S. attorneys remaining from the Obama
administration. \| Former Trump campaign adviser Roger Stone
acknowledges personal communication he had with Democratic National
Committee hacker Guccifer 2.0. \| Secretary of State Tillerson meets
with the Ambassadors to the United States of ASEAN Member States, as
well as Iraqi Minister of Oil Jabbar Al-Luaibi. \| Secretary of Health
and Human Services Tom Price announces his commitment to greater
Medicaid flexibility for states. \| Secretary of the Treasury Steven
Mnuchin announces the appointment of four senior staff. \| Secretary of
Defense Jim Mattis responds to the Armed Forces nude photo scandal,
calling the actions “unacceptable”. \|\| **51 \| 2017-03-11**: President
Trump meets with Secretary of Homeland Security John Kelly, Secretary of
the Treasury Steven Mnuchin, Secretary of Commerce Wilbur Ross and
Secretary of Veterans Affairs David Shulkin at the Trump National Golf
Club, where they discuss healthcare and the economy. \|\| **53 \|
2017-03-13**: President Trump signs Executive Order 13781, to reduce
operating costs of the federal government. \| President Trump expands
the power of the Central Intelligence Agency to make drone strikes. \|
Press Secretary Spicer states that Trump’s wiretapping tweet was
misinterpreted by the media, saying that Trump meant that the Obama
administration was responsible, not Obama personally. \| Secretary of
State Tillerson meets with the Foreign Ministers of Tunisia, Greece, and
Saudi Arabia. \|\| **54 \| 2017-03-14**: President Trump hosts Saudi
Deputy Crown Prince Mohammad bin Salman at the White House. \| Rachel
Maddow discloses a portion of Trump’s 2005 tax returns (both sides of
his Form 1040), mailed to David Cay Johnston by an unnamed source. The
form shows a payment of 38.4 million on a 49.5 million adjusted gross
income, accounting for 103.2 million in losses that year, with an
effective tax rate of 25%. The White House verifies the cited figures
and condemns the public release as “totally illegal”. \| Vice President
Pence swears in Seema Verma as Administrator of the Centers for Medicare
and Medicaid Services. Verma and Secretary of Health and Human Services
Price reemphasize their commitment to states’ roles in Medicaid
programs. \| Secretary of State Tillerson meets with United Arab
Emirates Foreign Minister Abdullah bin Zayed Al Nahyan. \|\| **55 \|
2017-03-15**: President Trump makes remarks at the American Center for
Mobility at Willow Run in Ypsilanti, Michigan and later holds a
political rally in Nashville, Tennessee, at which he criticizes the
court rulings against the travel ban. \| Rep. Nunes reports that the
House Intelligence Committee has not discovered any evidence supporting
Trump’s wiretapping claim. \| Federal Judge Watson issues a temporary
nationwide restraining order on the revised travel ban. \| The senate
confirms Dan Coats as Director of National Intelligence in a vote of
85-12. \| During a televised town hall event, Secretary of Health and
Human Services Price says that it should be up to individual states to
determine whether vaccinations should be required. \| Ambassador to the
United Nations Nikki Haley describes the idea of a Muslim ban as
“un-American”. \| Secretary of State Tillerson makes his first official
visit to Japan, to discuss the threats posed by North Korea’s missile
program. \|\| **56 \| 2017-03-16**: The Trump Administration releases a
preliminary draft of its 2018 budget request. The budget’s largest
relative increases in spending include the Departments of Defense,
Homeland Security, and Veterans Affairs, while the largest cuts apply to
the EPA, Foreign Aid, and the Departments of Labor and Agriculture, as
well as a 20 percent cut to National Institutes of Health. Trump also
signs a memorandum directed at Speaker of the House Paul Ryan requesting
additional funds for the departments of Defense and Homeland Security.
\| Secretary of Housing and Urban Development Carson responds to
President Trump’s proposed budget cuts to his department, saying it
“recognizes a greater role for State and local governments, and the
private sector to address community and economic development needs”. \|
President Trump holds a bilateral meeting with Taoiseach Enda Kenny at
the White House and announces his intention to visit the Republic of
Ireland during his presidency. \| Press Secretary Spicer repeats claims
made by Andrew Napolitano that Britain’s Government Communications
Headquarters (GCHQ) conducted espionage against Donald Trump. \|
Executive Order 13780 is scheduled to be put into effect. A second U.S.
federal judge, Theodore D. Chuang of Maryland, grants that state’s
motion for a temporary restraining order on President Trump’s revised
travel ban. \| Secretary of Homeland Security Kelly meets with Costa
Rican President Luis Guillermo Solis. \|\| **57 \| 2017-03-17**:
President Trump holds a bilateral meeting and joint press conference
with German Chancellor Angela Merkel at the White House. \| GCHQ denies
all involvement in the alleged wiretapping of Trump Tower, prompting the
Trump administration to issue a formal apology to the United Kingdom
with assurances that the allegation will not be repeated. \| Secretary
of State Tillerson visits South Korea to discuss international threats
and indicates the possibility of military action against North Korea. \|
The White House announces that it will appeal the Hawaii ruling against
the revised travel ban. \| Vice President Pence meets with Costa Rican
President Luis Guillermo Solis. \| President Trump proclaims March 19 as
the start of National Poison Prevention Week. \|\| **58 \| 2017-03-18**:
President Trump speaks by telephone with Brazilian President Michel
Temer and Chilean President Michelle Bachelet. \| Secretary of State
Tillerson meets with Chinese Foreign Minister Wang Yi in Beijing, to
discuss the North Korean missile program. \| Secretary of the Treasury
Mnuchin meets with G-20 country finance ministers, where he defends the
Trump administration’s trade policy of economic protectionism. \|\| **59
\| 2017-03-19**: German Defense Minister Ursula von der Leyen rejects a
statement by President Trump on 18 March that Germany owes a financial
debt to NATO. \| Secretary of State Tillerson completes his diplomatic
tour of eastern Asia with a meeting with Chinese President Xi Jinping in
Beijing. \|\| **60 \| 2017-03-20**: President Trump issues a tweet
rejecting allegations of collusion with Russia as “fake news”. \| In a
House Intelligence Committee hearing, FBI Director James Comey states
that their investigation of Russian influence on the presidential
election also covers possible links between Russia and Trump campaign
figures and that the FBI has no evidence of wiretapping against Trump.
\| President Trump meets with philanthropist Bill Gates. \| President
Trump holds a bilateral meeting with Iraqi Prime Minister Haider
al-Abadi at the White House. \| President Trump holds an evening
political rally in Louisville, Kentucky. \| President Trump nominates
Judge Amul Thapar to the Sixth Circuit Court of Appeals. \| The Senate
Judiciary Committee begins hearings on the nomination of Judge Neil M.
Gorsuch to the Supreme Court of the United States. \| President Trump
signs a memorandum which “delegate to the Secretary of State the
functions and authorities vested in the President by” the “Updated Plan
for Verification and Monitoring of Proliferation of Nuclear Weapons and
Fissile Material” section of the National Defense Authorization Act.
\|\| **61 \| 2017-03-21**: President Trump signs a bill which defines
the budget and objectives of NASA, including a crewed mission to Mars as
early as 2033. The draft 2018 budget expands support of public-private
partnerships for deep-space habitation, revives a supersonic flight
research program, strengthens NASA’s cybersecurity, increases focus on
planetary science and robotic exploration, cancels the Europa lander and
Asteroid Redirect Mission, terminates four Earth science missions, and
eliminates the NASA Office of Education, resulting in an overall 0.8%
budget decrease.:43-44 \| Congressman Devin Nunes, Chairman of the House
Intelligence Committee, secretly visits the White House grounds to
observe classified information concerning Trump’s allegations of
wiretapping. \| Secretary of State Tillerson meets with Honduran
President Juan Orlando Hernandez. \| President Trump proclaims March 21
as National Agriculture Day. \| The Department of Labor pushes back the
effective date of the Occupational Exposure to Beryllium rule by one
month. \|\| **62 \| 2017-03-22**: President Trump is briefed by Devin
Nunes, who also holds a news conference at the White House, on the
evidence concerning Trump’s wiretapping allegations which he was shown
on the White House grounds on the previous day. \| President Trump
offers British Prime Minister Theresa May the United States’ full
support, following a briefing by National Security Advisor McMaster on a
fatal terrorist attack carried out near the Palace of Westminster in
London. \| Secretary of State Tillerson hosts a summit of 68 nations in
Washington to discuss anti-ISIS strategy. \| Secretary of Homeland
Security Kelly meets with President of Honduras Juan Orlando Hernandez.
\|\| **63 \| 2017-03-23**: The first major Congressional vote on
President Trump’s planned repeal and replacement of the Affordable Care
Act is postponed until March 24. \| President Trump signs a memorandum
and a presidential notice to “continue the national emergency declared
in Executive Order 13664 with respect to South Sudan”. \| Secretary of
State Tillerson orders U.S. diplomatic missions to identify “populations
warranting increased scrutiny”. \|\| **64 \| 2017-03-24**: With the
consent of President Trump, House Speaker Paul Ryan indefinitely
postpones the first major Congressional vote on the repeal and
replacement of the Affordable Care Act, due to lack of support from both
sides of Congress. \| President Trump and Secretary of Defense Mattis
host a group of prior medal recipients at the White House on the eve of
National Medal of Honor Day. \| Under Secretary of State Shannon issues
a presidential permit to allow the construction of the Keystone XL
pipeline by TransCanada Corporation. \| President Trump proclaims March
25 as Greek Independence Day and hosts a celebration in the East Room.
\| Secretary of State Tillerson meets with the Foreign Minister of
Bahrain, Khalid bin Ahmed Al Khalifa. \| During a visit to the Osceola
County, Florida campus of Valencia College, Secretary of Education DeVos
says she is considering the extension of federal financial aid for
students that were year-round and interested in placing more focus on
community colleges. \| The Department of Labor pushes back the
Examinations of Working Places in Metal and Nonmetal Mines rule by two
months. \|\| **66 \| 2017-03-26**: Vice President Pence delivers an
evening speech to the American Israel Public Affairs Committee (AIPAC)
at Washington D.C.’s Verizon Center, reaffirming the United States’
commitments to Israeli defense, and to prevent Iran’s nuclear program
from producing a weapon. \|\| **67 \| 2017-03-27**: President Trump
signs a memorandum creating the White House Office of American
Innovation, consisting of 2 senior advisors and 8 assistants to the
president, to be headed by Jared Kushner. \| President Trump signs
Executive Order 13782, which revokes Executive Order 13673, section 3 of
Executive Order 13683, and Executive Order 13738. \| At the daily White
House press briefing, Attorney General Jeff Sessions outlines plans to
withhold funds and grants from sanctuary cities which refuse to fully
enforce federal immigration laws. \| President Trump signs four
Congressional Review Act disapproval resolutions into law, eliminating
regulations from the Obama administration. One repeals the Elementary
and Secondary Education Act. The second removes regulations on teacher
preparedness. The third deregulates resource management planning, and
the fourth nullifies the rule Federal Acquisition Regulation and Fair
Pay and Safe Workspaces. \|\| **68 \| 2017-03-28**: President Trump
signs Executive Order 13783, which removes a directive to consider
climate change during deliberations under the National Environmental
Policy Act, removes restrictions on fracking, and directs the
Environmental Protection Agency to suspend, revise or abolish the Clean
Power Plan. \| President Trump suggests cuts of 18 billion dollars to
mental health, foreign aid, public housing and others, including the
McGovern-Dole International Food for Education and Child Nutrition
Program. \| The President signs a bill ending the Fair Pay and Safe
Workplaces regulation. \| Press Secretary Spicer denies allegations that
the White House attempted to prevent former acting Attorney General
Sally Yates from testifying to the House Intelligence Committee. \| In a
lawsuit regarding The Apprentice, the President invokes the Supremacy
Clause. \| Secretary of State Tillerson meets with the foreign ministers
of Latvia, Lithuania, and Estonia. \| Secretary of the Interior Zinke
hosts media call about lifting the coal moratorium and American energy
independence. \| The Trump administration announced it would remove
“sexual orientation” and “gender identity” as proposed subjects for
possible inclusion on the Decennial Census and/or American Community
Survey in the future. \|\| **69 \| 2017-03-29**: President Trump signs
Executive Order 13784 to combat drug addiction and the opioid epidemic.
Trump also hosts a meeting in the Cabinet Room, concerning opioids and
drug abuse. \| President Trump issues a presidential notice continuing
Executive Order 13694, which “\[blocks\] the property of certain persons
engaging in significant malicious cyber-enabled activities”. \|
Secretary of the Interior Ryan Zinke signs a secretarial order scaling
back regulations on natural resources from the Obama administration. \|
Federal Judge Watson converts the temporary restraining order on
President Trump’s travel ban into an indefinite preliminary injunction,
citing evidence of a religious objective in violation of the
Establishment Clause. \| The White House verifies that Ivanka Trump is
to become an unpaid employee in the West Wing. \| Secretary of Education
Betsy DeVos delivers her first extended policy address at the Brookings
Institution, stating an interest in implementing choice policies and
criticizing policies from the Obama administration. \| Administrator of
the Environmental Protection Agency Scott Pruitt denies the
administrative petition by the Natural Resources Defense Council and the
Pesticide Action Network North America to ban Chlorpyrifos. \|\| **70 \|
2017-03-30**: President Trump calls FBI Director James Comey, asserts
that he wasn’t involved with Russian hookers and asks Comey to “lift the
cloud” of the Russia investigation. \| President Trump meets with Danish
Prime Minister Lars Lokke Rasmussen at the White House. \| The U.S.
Department of Justice issues a statement that it disagrees with Federal
Judge Watson’s March 29 ruling against the revised travel ban and that
it will continue its legal contest to reactivate the ban. \| Former
National Security Adviser Michael Flynn seeks immunity from the FBI in
exchange for testimony on White House links to Russia. \| Vice President
Pence casts his second tie-breaking vote, voting to advance a bill to
defund Planned Parenthood. \| Ambassador to the United Nations Nikki
Haley states that the priority of the United States policy concerning
Syrian President Bashar Assad is no longer to force him out of power. \|
Attorney General Jeff Sessions meets with Attorneys General of El
Salvador, Guatemala, and Honduras. \| Katie Walsh resigns as Deputy
Chief of Staff. \|\| **71 \| 2017-03-31**: Tom Price, the Secretary of
Health and Human Services, purchases 90,000 dollars worth of
pharmaceutical stocks a month before the signing of a bill which
benefits them. \| President Trump issues a tweet describing as a “witch
hunt” allegations of links between Russia and his associates, and
recommending that Michael Flynn requests immunity in return for
testimony to the intelligence authorities. \| President Trump signs two
executive orders aimed at preventing foreign trade abuses. The signing
occurs behind closed doors after Trump leaves the public ceremony
without signing the orders. \| President Trump signs Executive Order
13775, which provides an order of succession within the Department of
Justice. \| President Trump and Vice President Pence meet with former
Secretary of State Condoleezza Rice at the White House. \| The
Department of the Treasury announces new sanctions against North Korea
in response to Kim Jong Un’s continuing nuclear missile program. \|
District Judge David J. Hale rules against a freedom of speech defense
by President Trump’s lawyers, permitting to proceed a lawsuit in which
three plaintiffs allege that Trump incited violence at a presidential
campaign rally in 2016. \| President Trump proclaims April as the Month
of Cancer Control, Child Abuse Prevention, Sexual Assault Awareness,
Financial Capability, and Donate Life. Trump also proclaims April 2 as
Autism Awareness Day. \| President Trump nullifies a rule that limits
drug testing of state unemployment insurance holders. \| Secretary of
Transportation Chao announces 10 million for emergency repairs to
Atlanta’s collapsed I-85 overpass. \|\| **72 \| 2017-04-01**: Vice
President Mike Pence delivers a speech in Reynoldsburg, Ohio, remarking
on his continuing support for Supreme Court nominee Neil Gorsuch and
indicating that the campaign to repeal and replace the Affordable Care
Act remains ongoing. \| President Trump announces his intent to nominate
Mark Green as Secretary of the Army. \| Secretary of Defense James
Mattis visits the International Institute for Strategic Studies in
London. \|\| **73 \| 2017-04-02**: A federal judge rules that before the
presidency Trump may have incited violence at a rally in 2016 in
Kentucky. \| President Trump remarks in an interview that the U.S. may
take action against the North Korean nuclear missile program
independently of China. \| President Trump discusses healthcare reform
with Senator Rand Paul and White House Budget director Mick Mulvaney at
the Trump National Golf Club in Virginia. \| Jared Kushner travels to
Iraq over the weekend with the chairman of the Joint Chiefs of Staff,
Joseph Dunford. \|\| **74 \| 2017-04-03**: President Trump holds a
bilateral meeting with Egyptian President Abdel Fattah el-Sisi at the
White House, praising Sisi’s leadership and offering continuing support
for Egypt’s anti-terrorism measures. \| President Trump speaks by
telephone with Russian President Vladimir Putin to offer a message of
support following a fatal terrorist bombing on the Saint Petersburg
Metro. \| President Trump signs a congressional resolution allowing
Internet service providers to collect and sell their customers’ online
usage history with greater ease; he also signs three other bills. \|
President Trump orders an end to all funding to the United Nations
Population Fund. \| President Trump signs a memorandum to reform the
Military Selective Service Process. \| President Trump proclaims the
start of Crime Victims’ Rights Week. \| Press Secretary Sean Spicer
announces the donation of President Trump’s full quarterly salary
(78,333.32) to the National Park Service, following planned cuts. \| The
Department of the Interior proposes repealing the Consolidated Federal
Oil + Gas and Federal + Indian Coal Valuation Reform Rule. \| Secretary
of Homeland Security John F. Kelly meets with Salvadoran Foreign
Minister Hugo Martinez and President of the Legislative Assembly
Guillermo Gallegos. \|\| **75 \| 2017-04-04**: The Congressional Review
Act removes a requirement for employers to collect accurate records on
workplace accidents. \| The Justice Department orders a review of
consent decrees meant to limit police brutality. \| President Trump
delivers a speech to North America’s Building Trades Union (NABTU) at
the Washington Hilton, reiterating his intention to remove construction
regulations, and highlighting his approval of the new phase of the
Keystone Pipeline. \| Following a chemical attack in Syria which kills
numerous civilians, President Trump calls the attack “reprehensible” and
criticizes the Obama administration for not doing more to regulate
chemical weapons. \| North Korea launches a medium range ballistic
missile into the Sea of Japan. Secretary of State Rex Tillerson responds
by saying the U.S. has not changed its stance and does not comment
further. \| Reed Cordish, Assistant to the President for
Intergovernmental and Technology Initiatives, chairs a meeting at the
White House for business leaders, attended by President Trump and Vice
President Pence. \| President Trump directs emergency grazing on
Conservation Reserve Program lands located in Kansas, Oklahoma, and
Texas-the three states most heavily impacted by ongoing wildfires which
began on March 6, 2017. \| The Department of Labor responds to Trump’s
February 3 memorandum concerning the Fiduciary Duty Rule. \| The
Department of State cuts funding to the UN Population Fund, a fund
focused on reproductive health and family planning. \| The Justice and
Labor Departments cancel quarterly conference calls with LGBT
organizations. \|\| **76 \| 2017-04-05**: President Trump holds a
bilateral meeting and joint press conference with King Abdullah II of
Jordan at the White House, pledging to assist Jordan in eradicating ISIS
and in promoting peace between Israelis and Palestinians. \| President
Trump removes Steve Bannon from his position on the National Security
Council. \| President Trump suggests, offering no evidence, that former
National Security Advisor Susan Rice may have committed a crime by
seeking the names of the members of his team who may have been
incidentally mentioned on the intercepted communications of foreigners;
Rice denies the charge. \| President Trump issues a Presidential
Proclamation Honoring the Memory of John Glenn. \|\| **77 \|
2017-04-06**: President Trump orders a strike on the Shayrat Air Base in
Homs, Syria, using 59 Tomahawk cruise missiles in retaliation for the
chemical weapons attack on April 4. The strike is the first targeted
attack by the U.S. military on Ba’athist Syrian government forces since
the war began. Delivering a statement at Mar-a-Lago, Trump declares an
intent to protect American national security by deterring the use of
chemical weaponry. \| The President’s Republican Party changed the rules
of the Senate in order to confirm Neil Gorsuch, requiring only 51 votes
instead of the previous 60. \| Chinese President Xi Jinping is met at
Palm Beach International Airport by Secretary of State Tillerson.
Shortly following, he is escorted to Mar-a-Lago where President Trump
greets him upon arrival prior to a formal dinner. \| House Intelligence
Committee Chairman Devin Nunes recuses himself from the investigation
into Russian interference in the 2016 elections and is replaced by Mike
Conaway, after he is placed under investigation for possibly disclosing
classified information without authorization by the House Ethics
Committee. \| The Department of Labor delays enforcement of OSHA’s
Crystalline Silica Rule by three months. \| Secretary of the Interior
Zinke appoints Aurelia Skipwith as Deputy Assistant Secretary for Fish,
Wildlife and Parks, and Katharine MacGregor as Deputy Assistant
Secretary for Land and Minerals Management. \| President Trump proclaims
April 7 as Education and Sharing Day. \|\| **78 \| 2017-04-07**:
President Trump and Chinese President Xi Jinping continue talks during
the second day at Mar-a-Lago, concerning trade and North Korea.
President Xi leaves on schedule later on the same day. \| At an
emergency meeting of the United Nations Security Council in New York
City, U.S. Ambassador Nikki Haley warns that the U.S. is prepared to
take further action in Syria, and criticizes Russia and Iran for aiding
the regime of Bashar al-Assad. \| The senate confirms 113th Supreme
Court Justice Neil Gorsuch in a vote of 54-45, presided over by Vice
President Pence. \| The Department of Homeland Security orders Twitter
to reveal the identity of a user after their account had been critical
of the President and was suspected of working for the government. \|
President Trump proclaims April 14 as Pan American Day, April 9 through
April 15 as Pan American Week and April 9 as National Former Prisoner of
War Recognition Day, 2017. \|\| **79 \| 2017-04-08**: President Trump
sends a letter of notification to Congress concerning his recent missile
strike against Syrian government forces and indicating the possibility
of further action. \| President Trump speaks by telephone with the
Acting President of South Korea, Hwang Kyo-ahn. \|\| **80 \|
2017-04-09**: President Trump issues a statement on Twitter condemning a
pair of fatal terrorist bombings in the Egyptian cities of Tanta and
Alexandria and expressing his confidence in President Sisi’s ability to
respond. \| In an interview with CBS, Secretary of State Tillerson
suggests that the U.S. position and that of China on the North Korean
nuclear program are growing increasingly aligned. \| The Trump
administration announces that a Navy battle group headed by the aircraft
carrier USS Carl Vinson (CVN-70), diverting from plans to visit
Australian ports, is moving towards the Korean Peninsula. This statement
is later questioned following the publication four days later of
photographs of the carrier off the coast of Indonesia en route to the
Indian Ocean. \| K. T. McFarland is asked to step down as Deputy
National Security Adviser to become the U.S. Ambassador to Singapore.
\|\| **81 \| 2017-04-10**: President Trump conducts discussions on the
ongoing Syrian Civil War by telephone with British Prime Minister
Theresa May and German Chancellor Angela Merkel. \| Secretary of State
Tillerson attends a G7 meeting in Lucca, Italy. Secretary of Energy
Perry is in Rome for a G7 Energy ministerial meeting. \| Elaine Duke is
sworn in as Deputy Secretary for the Department of Homeland Security. \|
President Trump attends the swearing in of Neil Gorsuch as an Associate
Justice of the Supreme Court in a Rose Garden ceremony. \|\| **82 \|
2017-04-11**: The White House accuses Russia of attempting to cover up
the Khan Shaykhun chemical attack with the use of disinformation
tactics. \| Meeting with bankers and chief executives, President Trump
reiterates his pledge to reform or replace the rules imposed on Wall
Street following the Great Crash of 2008. \| Secretary of State
Tillerson declares in advance of a visit to Moscow that the rule of the
al-Assad family is ending. \| Press Secretary Spicer makes a televised
apology following controversial remarks made at a White House press
briefing concerning Adolf Hitler and the use of chemical weapons. \| The
President allegedly asks FBI Director James Comey to announce that the
Bureau was not investigating him. \| Secretary of Education Betsy DeVos
formally withdraws a pair of memoranda from the Obama administration
which required the office of Federal Student Aid to increase help for
Student Loan debtors. \|\| **83 \| 2017-04-12**: President Trump holds a
bilateral meeting and joint press conference with NATO Secretary General
Jens Stoltenberg at the White House, responding to perceived structural
changes within the organization by retracting his prior accusations of
NATO’s obsolescence. \| Secretary of State Tillerson meets Russian
Foreign Minister Sergey Lavrov in Moscow. At a joint press conference,
they agree to improve their relations with bilateral dialogue. Tillerson
later meets with President Putin at the Kremlin. \| The Education
Secretary Betsy DeVos rolls back student debt repayment protections. \|
President Trump indicates three major economic policy reversals: that he
would no longer label China as a currency manipulator; that he no longer
wanted to eliminate the Import-Export Bank; and that he may consider
reappointing Janet Yellen as chairwoman of the Federal Reserve. \|
President Trump and Budget Director Mulvaney lift the federal hiring
freeze. \|\| **84 \| 2017-04-13**: President Trump says “North Korea is
a problem. The problem will be taken care of,” expressing confidence
that Chinese President Xi Jinping will solve the problem. Trump issues a
tweet stating that if China fails to resolve the issue, the U.S. and its
allies will instead. \| A MOAB bomb is dropped on an ISIS cave complex
in Nangarhar Province, Afghanistan-the same province where Staff
Sergeant Mark De Alencar of 7th Special Forces Group was killed on April
8. \| The Department of the Treasury launches sanctions against ISIS
suppliers, and organizations of abusive prisons in Iran. \| President
Trump signs a bill into law nullifying a pending federal regulation that
would have disallowed states to withhold money from abortion providers.
\| Environmental Protection Agency (EPA) Administrator Scott Pruitt
announces sweeping “back-to-basics agenda” at the Harvey Mine in
Sycamore, Pennsylvania. The Agency announces plans to reconsider the ELG
rule, which aims to reduce steam electric power plant pollutants. \|\|
**85 \| 2017-04-14**: The Trump administration verifies that it will
discontinue the practice of voluntarily releasing the White House
visitors’ log, following the filing of a federal-court lawsuit on April
10 by a group of organizations, including CREW, demanding the
publication of such material under the Freedom of Information Act. \|
The President signs a bill allowing states to withhold funding from
Planned Parenthood. \| President Trump meets with two former Colombian
Presidents at his Mar-a-Lago resort to discuss the Colombian peace
process. \| CIA Director Mike Pompeo indicates that the U.S. may be
willing to take tougher action against Iran in light of international
security concerns over that country’s nuclear program. \| Under
Secretary of State Shannon meets with Mark P. Long of Western Digital.
\| The Department of the Treasury sanctions an Al-Nusra Front and
Al-Qaeda facilitator, and two Central African Republic militia
commanders. \| President Trump proclaims April 15 through April 23,
2017, as National Park Week. \| The Justice Department issues a
two-sentence court filing, saying it has dropped its lawsuit over North
Carolina’s “bathroom bill”. \|\| **86 \| 2017-04-15**: Tax Day March
rallies are held throughout the U.S. President Trump responds the
following day in two tweets, saying “the election is over.” \|\| **87 \|
2017-04-16**: President Trump claims that protests against him were paid
for. \| Vice President Pence arrives in South Korea at the start of an
Asia-Pacific diplomatic tour. Speaking in Seoul, Pence denounces as a
“provocation” a failed North Korean missile test carried out that
morning, and reiterates that the U.S. is committed to South Korean
defense. \|\| **88 \| 2017-04-17**: President Trump calls leader of
Turkey Recep Tayyip Erdogan to congratulate his victory in a referendum
increasing his powers, despite the State Department questioning the
democratic legitimacy of the poll. \| Vice President Pence visits the
Korean Demilitarized Zone near the South Korean city of Paju. In a
statement to the press, Pence declares an end to the “era of strategic
patience” concerning the North Korean missile program and demands that
they abandon their nuclear ambitions. \| President Trump and First Lady
Melania Trump participate in the White House Easter Egg Roll. \|\| **89
\| 2017-04-18**: President Trump visits the headquarters of tool
manufacturer Snap-on in Kenosha, Wisconsin, to sign Executive Order
13788, which intends to prevent abuse of the H-1B visa program and to
give preference to U.S.-made products. \| Secretary of Homeland Security
John F. Kelly says President Trump’s critics should “shut up and support
the men and women on the front lines”. \| Vice President Pence arrives
in Tokyo, Japan, as part of an Asia-Pacific tour. \| Secretary of
Defense James Mattis travels to Saudi Arabia to discuss security in the
region. \|\| **90 \| 2017-04-19**: President Trump signs a bill into law
extending the Veterans’ Access to Care through Choice, Accountability,
and Transparency Act of 2014. \| President Trump hosts the Super Bowl LI
champions New England Patriots at the White House. \| Vice President
Pence delivers a speech aboard the USS Ronald Reagan (CVN-76) moored at
Yokosuka, Japan, to 2,500 members of U.S. and Japanese armed forces,
condemning North Korea’s threat to international security and stating
that America’s “shield stands guard and sword stands ready”. \|\| **91
\| 2017-04-20**: President Trump signs a memorandum directing the
Department of Commerce to begin an investigation on whether steel
imports are a threat to U.S. national security, and another which
provides initial reports on the implementation of the Global Magnitsky
Human Rights Accountability Act. \| The President’s lawyers argue that
protesters at his rallies had “no rights” to “express dissenting views”
because their First Amendment rights did not apply “as part of the
campaign rally of the political candidates they oppose”. \| President
Trump holds a bilateral meeting and joint press conference with Italian
Prime Minister Paolo Gentiloni at the White House. \| President Trump’s
self-imposed deadline for production of a full White House report into
Russian interference in the 2016 election expires unfulfilled. \| Vice
President Pence takes part in a joint press conference with President
Joko Widodo at Indonesia’s State Palace in Jakarta. \| Secretary of
Defense Mattis travels to Egypt to discuss security in the region and
participates in a wreath-laying ceremony at the Unknown Soldier
Memorial. \|\| **92 \| 2017-04-21**: President Trump signs one executive
order and two memorandums. The executive order directs Treasury
Secretary Steven Mnuchin to review the U.S. tax code to recommend
unnecessary regulations to remove, and the two memorandums direct the
Treasury Secretary to review portions of the Dodd-Frank Wall Street
Reform and Consumer Protection Act. \| On the final leg of his
Asia-Pacific diplomatic tour, Vice President Pence is met at Sydney
Airport by Australian Deputy Prime Minister Barnaby Joyce. \| President
Trump appoints Rear Admiral Sylvia Trent-Adams as acting Surgeon General
to replace Vivek Murthy. \| Secretary of Defense Mattis visits Israel to
meet with President Reuben Rivlin, Prime Minister Netanyahu and Minister
of Defense Avigdor Lieberman, and participates in a wreath-laying
ceremony at the World Holocaust Remembrance Center. \|\| **93 \|
2017-04-22**: President Trump and First Lady Melania Trump visit the
Walter Reed National Military Medical Center in Maryland to award the
Purple Heart to Sergeant First Class Alvaro Barrientos. \| Vice
President Pence meets Australian Prime Minister Malcolm Turnbull at
Kirribilli House. At a later joint press conference at Admiralty House,
Pence says the U.S. will honor a refugee deal with Australia; a deal
previously described by President Trump as “dumb”, and which led to a
truncated phone call on February 1. \| Secretary of Defense Mattis
travels to Qatar to discuss security in the region. \|\| **94 \|
2017-04-23**: In response to polls showing the latest approval rating of
any president since 1945, President Trump blames “fake news”. \|
President Trump issues a video address to coincide with Israel’s
Holocaust Memorial Day in which he condemns all antisemitism, past and
present. \| Attorney General Jeff Sessions says that DREAMers are
subject to deportation. \| Secretary of Defense Mattis travels to
Djibouti to meet with President Ismail Omar Guelleh to discuss security
in the region. \|\| **95 \| 2017-04-24**: It is revealed that former
National Security Advisor Michael Flynn had failed to disclose a 33,000
payment from Russia Today while in the president’s service. \| The
Anti-Defamation League reports an 86% rise in anti-Semitic attacks since
the president’s inauguration. \| Vice President Pence completes his tour
of the Asia-Pacific with an address to 200 U.S. troops and officials at
Pago Pago, American Samoa, followed by a brief stop at Joint Base Pearl
Harbor-Hickam in Hawaii during his return to Washington D.C. \| Treasury
Secretary Steven Mnuchin announces new sanctions against the Syrian
government in response to the chemical weapons attack on April 4. \| The
Senate confirms Sonny Perdue as the 31st Secretary of Agriculture in a
vote of 87-11. \| The Department of Commerce orders a 20% tariff on
lumber imports from Canada, worth about 1 billion. \|\| **96 \|
2017-04-25**: The president publicly suggests breaking up the United
States Court of Appeals for the Ninth Circuit after it block his
defunding of sanctuary cities. \| Sonny Perdue is sworn in as the 31st
Secretary of Agriculture.\[citation needed\] \| President Trump speaks
at the U.S. Capitol for the Holocaust Memorial Museum (USHMM) “Days of
Remembrance” event. \| President Trump signs an executive order,
“Promoting Agriculture and Rural Prosperity in America”. The executive
order instructs the Secretary of Agriculture to chair an interagency
task force to examine legislative, regulatory, and policy changes in
support of rural America. \| U.S. District Judge William Orrick III
issues a preliminary injunction blocking President Trump’s Executive
Order 13768 of 25 January, which ordered the withholding of federal
funds from cities which refuse to comply with federal immigration
enforcement measures. \|\| **97 \| 2017-04-26**: President Trump
welcomes the Senate to the Eisenhower Executive Office Building prior to
their briefing with the Secretary of Defense, State, Director of
National Intelligence, and chairman of the Joint Chiefs of Staff on the
issue of North Korea. Pence and the four officials brief the House of
Representatives at the Capitol complex later in the day. \| Steve
Mnuchin and Gary Cohn release President Trump’s tax-reform outline plan,
the proposals of which include among other items a cut in the rate of
business tax from 35% to 15%, a simplification of the tax system by
reducing seven existing tax brackets to three, and the elimination of
the alternative minimum tax. \| President Trump signs a pair of
executive orders for reviews of national monuments and of public
schools. \| Secretary of State Tillerson and Secretary of Defense Mattis
lead a briefing on North Korea for members of the house and senate. \|\|
**98 \| 2017-04-27**: Speaking at the Oval Office, President Trump
praises President Xi Jinping’s diplomacy in respect of North Korea but
warns of the continuing possibility of a “major, major conflict”. \|
President Trump holds a bilateral meeting with Argentine President
Mauricio Macri at the White House. \| A renewed attempt to secure a
Congressional vote on President Trump’s plan to repeal and replace the
Affordable Care Act is abandoned. \| The Senate confirms Alex Acosta as
the 28th Secretary of Labor in a vote of 60-38.\[citation needed\] \|\|
**99 \| 2017-04-28**: Alex Acosta is sworn in as the 28th Secretary of
Labor.\[citation needed\] \| At the Georgia World Congress Center in
Atlanta, President Trump delivers the first presidential address to the
National Rifle Association since 1983, reiterating his guarantee of the
Second Amendment. \| The EPA removes all references to climate change
from their website. \| Speaking at a meeting of the U.N. Security
Council, Secretary of State Tillerson calls for support from the
international community to limit the North Korean missile program,
warning that the U.S. mainland may soon be in range and that inaction
may have “catastrophic consequences”. \|\| **100 \| 2017-04-29**: North
Korea conducts another missile test from Bukchang, which fails shortly
after liftoff. President Trump condemns this action as an insult to
China. \| The president falsely claims that the new Republican health
care bill would protect health insurance for those with pre-existing
conditions. \| President Trump speaks by telephone with Philippine
President Rodrigo Duterte to discuss North Korea, following a series of
missile tests. Trump invites Duterte to meet him at the White House,
drawing criticism from international human rights organizations due to
concerns regarding the latter’s drug war. \| President Trump forgoes the
White House Correspondents’ Association dinner in favor of an evening
political rally in Harrisburg, Pennsylvania, with Vice President Pence
and various cabinet members. \|\| **101 \| 2017-04-30**: CBS publishes
an interview from April 29 in which President Trump suggests that China
may have been responsible for the 2016 Democratic National Committee
email leak. \| The president extends an invitation to Rodrigo Duterte to
visit the White House. \|\| **102 \| 2017-05-01**: In an interview with
Bloomberg News, President Trump expresses an openness to meet with North
Korean leader Kim Jong-un under the right circumstances. \| The Trump
international Hotel in Washington D.C. receives 30,000 from a Turkish
interest group. \| The president ends an interview when pressed on
evidence of being wiretapped by Obama. \| The president praises Andrew
Jackson, organiser of the Trail of Tears, during an interview, saying he
had “a big heart”. \| Press Secretary Spicer confirms that Congress is
currently under whip in preparation for a new attempt to secure a vote
on President Trump’s plan to repeal and replace the Affordable Care Act.
\| The White House defunds Let Girls Learn, a program initiated by
former First Lady Michelle Obama. \| The Department of Agriculture
abandons Obama-era standards for healthier school lunches. \|\| **103 \|
2017-05-02**: President Trump speaks by telephone with Russian President
Vladimir Putin for the first time since the Khan Shaykhun chemical
attack. They discuss the ongoing Syrian Civil War, Middle Eastern
terrorism, and issues concerning the North Korean nuclear missile
program, and agree to meet in person. \| The president refers to the
separation of powers as an “archaic” system. \| In a pair of tweets,
President Trump suggests the abandonment of existing supermajority
voting rules in the Senate, in favor of the principle of simple
majority. \| Secretary of State Tillerson delivers remarks at the Model
United Nations Conference at the State Department. \| The president
appoints Teresa Manning, an anti-abortion activist, in charge of family
planning for low-income people. \| The Department of Health and Human
Services announces a plan to roll back regulations interpreting the
Affordable Care Act’s nondiscrimination provisions to protect
transgender people. \|\| **104 \| 2017-05-03**: President Trump holds a
bilateral meeting and joint press conference with Palestinian President
Mahmoud Abbas at the White House. \|\| **105 \| 2017-05-04**: President
Trump holds a bilateral meeting with Australian Prime Minister Malcolm
Turnbull at the Intrepid Sea, Air + Space Museum, in Trump’s first
return to New York since his inauguration. \| Vice President Pence
speaks at a Cinco de Mayo celebration at the Eisenhower Executive Office
Building. \| The House of Representatives votes 217-213 in favor of
repealing and replacing major parts of the Affordable Care Act. \|
Environmental Protection Agency (EPA) Administrator Pruitt recuses
himself from a number of lawsuits which he had helped to bring against
the EPA. \|\| **106 \| 2017-05-05**: Mark Green withdraws from President
Trump’s nomination for the position of Secretary of the Army following
prior controversial remarks made by Green concerning Muslims and
concerning the LGBT community. \| At least five scientists on the Board
of Scientific Counselors are informed by the Environmental Protection
Agency that their terms will not be renewed. \|\| **107 \| 2017-05-06**:
Sister of Jared Kushner, the president’s advisor and son-in-law,
solicits investments from Chinese business owners in return for American
visas. \|\| **108 \| 2017-05-07**: President Trump tweets a message of
congratulation to Emmanuel Macron following his victory over Marine Le
Pen in the French presidential election. \|\| **109 \| 2017-05-08**:
President Trump and French President-elect Emmanuel Macron speak by
telephone and arrange to meet during a NATO summit scheduled for 25 May
in Belgium. \| President Trump issues a series of tweets which describe
allegations of collusion with Russia as a hoax, and which suggest that
the ongoing investigations are a waste of taxpayers’ money. \| Former
acting Attorney General Sally Yates and former Director of National
Intelligence James Clapper testify before the Senate Judiciary
Committee’s Crime and Terrorism subcommittee about Russian interference
in the 2016 presidential election. Yates asserts that the Trump
administration knew that former National Security Advisor Michael T.
Flynn was vulnerable to Russian blackmail at least 18 days before he was
dismissed. Clapper says he was unaware of the FBI investigation into
Russian electoral interference during his tenure. \| The EPA fires half
the scientists on its advisory board. \| White House officials call the
office of Justin Trudeau in a bid to prevent an executive order from
cancelling NAFTA. \| Secretary of Defense Mattis visits Copenhagen, to
meet with representatives from 15 countries leading the campaign against
ISIS. Mattis also meets Danish Minister of Defense Claus Hjort
Frederiksen to discuss European security and NATO alliance, and Prime
Minister Lars Lokke Rasmussen to re-affirm the close ties between
Denmark and the U.S. \|\| **110 \| 2017-05-09**: President Trump removes
James Comey from his position as FBI Director. The White House explains
that it is acting on the recommendation of Deputy Attorney General Rod
Rosenstein and Attorney General Sessions, citing Comey’s public
statements about the Clinton email investigation as the reason for the
decision. \| Andrew G. McCabe becomes acting Director of the FBI. \| In
an interview with CNN, President Trump’s Counselor Kellyanne Conway
denies that Comey’s dismissal is part of a White House cover-up. \|
Journalist Dan Heyman is arrested after questioning Secretary of Health
and Human Services Tom Price. \| Secretary of State Tillerson signs an
agreement that expands the sharing of intelligence between the U.S. and
Georgia. \|\| **111 \| 2017-05-10**: Following a separate meeting
between Russian Foreign Minister Sergey Lavrov and Secretary of State
Tillerson at the State Department earlier in the day, President Trump
meets with Lavrov and Russian Ambassador Sergey Kislyak in the Oval
Office; a meeting at which Trump divulges classified information. He
also notes to them that “I faced great pressure because of Russia.
That’s taken off.” \| President Trump meets with former Secretary of
State Henry Kissinger at the White House. \| Vice President Pence
describes Trump’s dismissal of James Comey as “the right decision at the
right time”. \| Secretary of Defense Mattis attends the Somalia
Conference in London. \|\| **112 \| 2017-05-11**: President Trump signs
an executive order to initiate an investigation of allegations of voter
fraud during the 2016 U.S. presidential election, under a commission to
be chaired by Vice President Pence. Kansas Secretary of State Kris
Kobach, a prominent proponent of strict voter ID laws, is appointed
vice-chair and will administer day-to-day operations. \| In an interview
with NBC, President Trump explains that he had decided to dismiss James
Comey prior to and without regard to a recommendation from the Attorney
General’s office. He also reveals of his reasoning that: “Then I decided
to just do it, said to myself, I said: This Russia thing with Trump and
Russia is a made-up story, it’s an excuse by the Democrats for having
lost an election that they should’ve won.” \| Vice President Pence
delivers a speech to a Billy Graham Evangelistic Association meeting at
the Mayflower Hotel in Washington D.C., calling for ISIS attacks on
Christians to be labeled “genocide”. \| Secretary of State Tillerson
attends an Arctic Council meeting in Fairbanks, Alaska. \|\| **113 \|
2017-05-12**: President Trump suggests on Twitter and in an interview
broadcast on 13 May the possibility of ceasing the practice of White
House press briefings in favor of written statements. \| President Trump
tweets a warning to Comey that he ought to “hope that there are no
‘tapes’ of our conversations before he starts leaking to the press”.
When questioned at the daily briefing, Press Secretary Spicer does not
confirm or deny that conversations at the White House have been
recorded. \| A law firm finds after reviewing ten years of the
president’s tax returns that with a “few exceptions”, he has no
financial ties to Russia. \| Vice President Pence visits Billings,
Montana to campaign for Greg Gianforte in the special election for
Montana’s congressional seat. \|\| **114 \| 2017-05-13**: The EPA
announces an end to mining restrictions on Alaskan headwaters. \| At
Virginia’s Liberty University, President Trump delivers his first
college commencement speech as sitting president, with the theme of
perseverance. During the graduation speech he was awarded an Honorary
Doctor of Laws degree. \|\| **115 \| 2017-05-14**: The White House
describes North Korea as a “flagrant menace” in response to the
test-launch of a missile from near Kusung into the Sea of Japan. \|\|
**116 \| 2017-05-15**: President Trump delivers a speech at the 36th
Annual National Peace Officers’ Memorial Service at the Capitol
Building, reiterating his support for the police service. \| President
Trump hosts the crown prince of Abu Dhabi, Mohammed bin Zayed Al Nahyan,
at the White House. \| National Security Advisor H.R. McMaster and
Secretary of State Tillerson issue denials to allegations that President
Trump shared certain classified information with Lavrov and Kislyak on
May 10, 2017. \| Three 9th Circuit judges hold a hearing in Seattle,
Washington, for arguments relating to President Trump’s currently barred
travel ban. \|\| **117 \| 2017-05-16**: President Trump holds a
bilateral meeting and joint press conference with Turkish President
Recep Tayyip Erdogan at the White House. \| President Trump issues a
pair of tweets explaining that he has a right to share information with
Russia for counter-terrorism reasons. \| National Security Advisor
McMaster holds a White House press briefing at which he describes the
President’s conversation with Lavrov and Kislyak as “wholly
appropriate”. \| The White House issues a denial that President Trump
asked Comey on February 14, 2017, to end the FBI investigation into
Michael Flynn. House Oversight Committee Chair Jason Chaffetz requests
from the FBI all material on Comey’s meetings with Trump. \|\| **118 \|
2017-05-17**: President Trump delivers the commencement address at the
Coast Guard Academy in New London, Connecticut, with a speech on the
theme of persistence, claiming that “No politician-and I say this with
great surety-has been treated worse or more unfairly.” \| Vice President
Pence becomes the first sitting vice president to form a political
action committee, filing paperwork to create the Great America
Committee. \| Deputy Attorney General Rosenstein appoints Robert Mueller
as a special prosecutor to investigate alleged Russian interference in
the 2016 presidential election. According to reporting by The New York
Times in January 2018, President Trump attempts to dismiss Mueller
before the end of June, but retreats upon the threatened resignation of
White House counsel Don McGahn. \|\| **119 \| 2017-05-18**: President
Trump holds a bilateral meeting and joint press conference with
Colombian President Juan Manuel Santos at the White House. \| At the
press conference, President Trump denies telling Comey to end the FBI
investigation into Michael Flynn, denies any collusion between his
campaign and Russia, and reiterates his claim that he is the subject of
a “witch hunt”. \| Vice President Pence denies that he knew prior to
March 2017 that Flynn was under federal investigation. \| White House
Director of Communications, Michael Dubke, resigns, agreeing to continue
in his position at least until the end of President Trump’s upcoming
foreign visit. \| Following a private Senate briefing by Deputy Attorney
General Rosenstein, three Senators confirm that Rosenstein believed
President Trump planned to dismiss Comey prior to Rosenstein’s
recommendation. \|\| **120 \| 2017-05-19**: President Trump leaves
Washington D.C. for Saudi Arabia on his first official foreign tour. \|
The White House does not dispute reports that President Trump called
former FBI Director Comey a “nut job” and said that firing him “relieved
pressure” in a meeting with Russian officials. Press Secretary Spicer
accuses Comey of “grandstanding” and impeding the relationship with
Russia. \| There are reportedly still 700 unfilled positions at the
Centers for Disease Control and Prevention. \|\| **121 \| 2017-05-20**:
President Trump is received in Riyadh by Salman bin Abdulaziz Al Saud
and is awarded Saudi Arabia’s highest civilian honor, the Collar of
Abdulaziz Al Saud. \| President Trump signs an arms deal worth more than
350 billion and various other investment agreements with Saudi Arabia.
\|\| **122 \| 2017-05-21**: The president suggests cutting US1.7
trillion over ten years from redistributive programs such as food stamps
and Medicaid. \| President Trump delivers a speech to more than fifty
leaders of Muslim-majority nations at an Arab Islamic American Summit at
the King Abdulaziz Conference Centre in Riyadh, condemning the alleged
funding of terrorism by Iran. \| President Trump holds several bilateral
meetings with the President of Egypt Abdel Fattah el-Sisi, the King of
Bahrain Hamad bin Isa Al Khalifa and the Emir of Qatar Tamim bin Hamad
Al Thani. \| Vice President Pence delivers the commencement speech at
the University of Notre Dame’s graduation ceremony in South Bend,
Indiana. \|\| **123 \| 2017-05-22**: Continuing his tour of the Middle
East and Europe, President Trump is met in Tel Aviv by Israeli Prime
Minister Netanyahu and President Reuven Rivlin. He visits the Church of
the Holy Sepulchre in Jerusalem and becomes the first sitting U.S.
president to visit the Western Wall. \| Health insurance providers have
raised premiums by up to 50% due to uncertainty surrounding the
administration’s stance towards the Affordable Care Act. \|\| **124 \|
2017-05-23**: President Trump pays his respects at the Jewish Holocaust
memorial Yad Vashem with Prime Minister Netanyahu. \| President Trump
visits Bethlehem in the West Bank to hold a bilateral meeting with
Palestinian leader Mahmoud Abbas. Speaking to the press alongside Abbas,
Trump condemns the fatal terrorist bombing of England’s Manchester Arena
on the previous night, calling the perpetrators “losers”. \| President
Trump lands in Rome, Italy, in advance of a visit to the Vatican. \| The
White House publishes President Trump’s first full budget proposal.
Allocations include 1.6 billion for a Mexican border wall and a 10%
increase in military spending. Reductions include an 800 billion cut to
Medicaid, a 190 billion cut to food stamps, cuts to Meals on Wheels and
drug treatment programs, and the elimination of student loan subsidies.
The budget assumes economic growth of 3% to avoid adding to the deficit.
\|\| **125 \| 2017-05-24**: President Trump meets privately with Pope
Francis at Vatican City. \| President Trump holds bilateral meetings
with Italian President Sergio Mattarella and Prime Minister Paolo
Gentiloni, praising Italy’s efforts in combating terrorism. \| President
Trump flies in the afternoon to Brussels to meet with Belgian Prime
Minister Charles Michel in advance of a NATO summit, following which he
had an audience with Belgian King Philippe and Queen Mathilde. \|
Secretary of Housing and Urban development Ben Carson calls poverty “a
state of mind”. \|\| **126 \| 2017-05-25**: President Trump meets with
European Council President Donald Tusk and European Commission President
Jean-Claude Juncker at the European Council headquarters.\[citation
needed\] \| During a NATO meeting, the president visibly pushes the
Montenegrin Prime Minister Dusko Markovic during a photo-op. \|
President Trump hosts a lunch meeting with French President Emmanuel
Macron at the U.S. ambassador’s residence in Brussels. \| At the new
NATO headquarters President Trump unveils a memorial to the September 11
attacks. In a speech to NATO leaders, President Trump criticizes member
states for their levels of defence spending and receives a commitment
from NATO to formally join the international anti-ISIS coalition. \| The
federal appeals court in Richmond, Virginia, refuses to reinstate
President Trump’s travel ban, citing religious discrimination. The
Justice Department declares an intent to appeal to the Supreme Court.
\|\| **127 \| 2017-05-26**: President Trump attends the 43rd G7 summit
with world leaders of G7 in Taormina, Italy to discuss world issues such
as trade, climate change and the migration crisis. Trump criticizes the
large imports of German automobiles, pointing to the large U.S. trade
deficit with Germany. Trump refuses to commit the U.S. to the Paris
Agreement on climate change and cutting greenhouse emissions. \|
President Trump holds a bilateral meeting with Japanese Prime Minister
Shinzo Abe to discuss the threat of North Korea’s ballistic missile
program. \| Secretary of State Tillerson meets with Secretary Johnson in
London with regards to the Manchester Arena bombing that occurred on May
22. \|\| **128 \| 2017-05-27**: President Trump continues discussions
with G7 leaders on a whole range of issues, agreeing on a communique on
fighting protectionism in international trade, but disagreeing with a
majority of a leaders on endorsing the Paris climate change accord. \|
President Trump addresses American troops stationed in Italy at the
Naval Air Station Sigonella before leaving for the U.S. \| At a press
briefing, National Security Advisor McMaster remarks that he “would not
be concerned”, when responding to questions about a recent report that
Kushner had discussed with Kislyak the possibility of creating a secret
communication channel between President Trump’s team and the Kremlin.
\|\| **129 \| 2017-05-28**: President Trump issues an extended series of
tweets, describing many recent White House leaks as ‘fake news’, and
questioning the use of anonymous sources by the media. \| President
Trump is briefed on a new missile test-launch by North Korea, which is
alleged to have discharged into waters within Japan’s exclusive economic
zone. \| Answering questions concerning reports of an attempt by the
Trump team to set up a secret line of communication with the Kremlin,
Homeland Security Secretary Kelly states, “Any channel of
communications, back or otherwise, is a good thing.” \|\| **130 \|
2017-05-29**: President Trump performs a wreath-laying ceremony at the
Tomb of the Unknown Soldier at the Arlington National Cemetery and gives
a speech honoring those who have died fighting for the U.S., giving
special mention to the fallen son of Homeland Security Secretary Kelly.
\| Vice President Pence hosts more than 200 bicycle-riders at the annual
Project Hero Memorial Day Bike Ride at the Vice President’s residence.
\|\| **131 \| 2017-05-30**: President Trump reiterates on Twitter his
proposal to abandon the Senate’s tradition of supermajority voting, in
order to accelerate legislation. \| The resignation (tendered 18 May) of
President Trump’s Director of Communications, Michael Dubke, is
confirmed. \|\| **132 \| 2017-05-31**: The White House grants ethics
waivers to 17 senior officials. \| President Trump holds a bilateral
meeting with Vietnamese Prime Minister Nguyen Xuan Phuc at the White
House and oversees the signing of trade deals worth 17 billion. \| The
administration starts asking for five years of social media activity on
visa applications. \| The president uses the word covfefe in a tweet. \|
Press Secretary Spicer announces that all press questions concerning the
ongoing investigation into the administration’s alleged ties to Russia
will henceforth be referred to President Trump’s lawyer, Marc Kasowitz.
\| Secretary of Veteran Affairs David Shulkin gives a press briefing
concerning problems facing his department. \|\| **133 \| 2017-06-01**:
President Trump formally announces his intent to withdraw the U.S. from
the 2015 Paris climate agreement, prompting criticism from former and
serving world leaders and the United Nations.Tesla’s Elon Musk and
Disney CEO Bob Iger resign from the president’s business advisory
council in protest. \| The Justice Department appeals to the Supreme
Court to reinstate President Trump’s travel ban. \| President Trump
signs the long-standing waiver resolving not to move the U.S. embassy in
Israel from Tel Aviv to Jerusalem. \|\| **134 \| 2017-06-02**: President
Trump signs The American Law Enforcement Heroes Act to provide federal
grants to those federal and state law enforcement agencies that hire and
train veterans; and The Public Safety Officers’ Benefits Improvement Act
that reduces the backlog of families awaiting approval of survivor
benefits of public safety officers killed in the line of duty. \|\|
**135 \| 2017-06-03**: President Trump issues a pair of tweets sending a
message of support to the UK and promoting his administration’s halted
travel ban following a briefing on a major terrorist incident in London.
\|\| **136 \| 2017-06-04**: On Twitter, President Trump criticizes
London Mayor Sadiq Khan’s response to the terrorist incident, drawing
condemnation from members of the UK’s governing and opposition parties,
including British Prime Minister Theresa May. \| President Trump
delivers an evening speech at the Ford’s Theater’s annual fundraising
gala, remarking on international security questions and denouncing the
London terror attack of June 3. \|\| **137 \| 2017-06-05**: The American
ambassador to China resigns in response to the country leaving the Paris
Agreement. \| President Trump announces plans to modernize and privatize
the U.S. air traffic control system. \| In a series of tweets, President
Trump praises his initial “travel ban”, and blames the Justice
Department for the “watered-down” revised version he signed on March 6.
\| Speaking publicly during a diplomatic visit to Australia with
Secretary of Defense Mattis, Secretary of State Tillerson suggests that
China ought to take stronger action to prevent North Korea from
developing a nuclear missile. \|\| **138 \| 2017-06-06**: President
Trump claims credit for helping to instigate the recent severing of
diplomatic ties by Saudi Arabia, Bahrain, the UAE, Yemen, eastern Libya
and the Maldives with the state of Qatar over allegations of terrorist
funding. \| Secretary of State Tillerson arrives in Wellington, New
Zealand, for bilateral talks with Prime Minister Bill English and
Minister of Foreign Affairs Gerry Brownlee. \| Press Secretary Spicer
confirms that President Trump’s tweets are to be “considered official
statements by the President of the United States”. \|\| **139 \|
2017-06-07**: President Trump announces his nomination of Christopher A.
Wray for the directorship of the FBI. \| President Trump gives a speech
in Cincinnati, Ohio, detailing government plans to overhaul the nation’s
infrastructure and replace Obamacare. \| At a Senate Intelligence
Committee hearing, DNI Dan Coats and NSA Director Michael S. Rogers
testify that they never felt inappropriate pressure from President Trump
but decline to answer questions on private conversations with him. \|\|
**140 \| 2017-06-08**: President Trump addresses the Faith and Freedom
Coalition’s annual conference in Washington. \| James Comey testifies to
the Senate Intelligence Committee in an open hearing in which he
reiterates his statement that President Trump was not under
investigation by the FBI during his tenure, but he does not explicitly
confirm whether or not he considers the President to have obstructed any
investigation. He confirms that Michael Flynn was under criminal
investigation prior to his removal from the administration. \|\| **141
\| 2017-06-09**: President Trump announces in a speech at the Department
of Transportation that he will set up a special council to speed up the
permit process to build roads and bridges. \| President Trump holds a
bilateral meeting and joint press conference with Romanian President
Klaus Iohannis at the White House, discussing issues such as NATO, and
accusing James Comey of lying under oath on June 8. \|\| **144 \|
2017-06-12**: President Trump holds his first full cabinet meeting at
the White House since his inauguration, blaming the Democrats for
delaying some of his nominees. \| President Trump hosts the NCAA
champions Clemson Tigers at the White House. \| The Attorneys General of
Maryland and the District of Columbia file a lawsuit against President
Trump, alleging violation of the emoluments clause. \| A second federal
court rejects President Trump’s appeal to lift the injunction against
Executive Order 13780, citing a lack of ‘sufficient justification’ for
the travel ban. \|\| **145 \| 2017-06-13**: President Trump hosts a
luncheon at the White House with Republican senators to discuss
repealing the Affordable Care Act. \| It is reported that 70% of Trump
Organisation properties sold since the election have been to anonymous
LLC’s, while before the election the figure was 2%. \| The president
blocks VoteVets, a veterans group representing 50,000 veterans, on
Twitter. \| President Trump promotes opening technical apprenticeships
to teenagers in a workforce development roundtable discussion in
Milwaukee, Wisconsin. \| Attorney General Sessions testifies to the
Senate Intelligence Committee on matters related to alleged Russian
interference in the 2016 U.S. presidential election. \|\| **146 \|
2017-06-14**: Special counsel Robert Mueller is conducting an
investigation into whether the president obstructed justice. \|
President Trump and Vice President Pence send messages of support to
those affected by a shooting incident in Alexandria, Virginia. \| Almost
200 Congressional Democrats file against President Trump a third lawsuit
alleging violation of the Foreign Emoluments Clause, the ongoing suits
being D.C. and Maryland v. Trump and CREW v. Trump. \| The Department of
Education withdraws its finding that an Ohio school district
discriminated against a transgender girl. \|\| **147 \| 2017-06-15**:
President Trump and First Lady Melania Trump visit congressman Steve
Scalise, who was critically wounded in the Virginia shooting incident a
day earlier. \| President Trump describes on Twitter alleged collusion
with Russia as a “phony story” in response to reports that he has been
under investigation for possible obstruction of justice following the
dismissal of James Comey on May 9. \| The president appoints Eric
Trump’s wedding planner to run federal housing in New York. \| DNI Dan
Coats meets with the Senate Intelligence Committee in closed session to
address issues from his testimony of June 7. \| President Trump signs an
executive order promoting apprenticeships, increasing the funding for
job-training programs by 5.5%, and giving more freedom to third-party
companies and schools to craft these programs. \| President Trump and
First lady Melania Trump attend the investiture ceremony of Justice Neil
Gorsuch at the Supreme Court. \|\| **148 \| 2017-06-16**: The
administration partially rolls back the thawing of ties with Cuba. \|
The White House tries to lessen the severity of a sanctions bill on
Russia. \| Deputy Assistant Secretary for Strategic Operations and
Outreach in the Office for Civil Rights (OCR) of the U.S. Department of
Education (and the Office’s Acting Assistant Secretary) Candice Jackson
releases new guidelines regarding bathroom policy for transgender
students. \| In a Twitter post, President Trump confirms that he is
under investigation for obstruction of justice, reiterating his claim
that it is a ‘witch hunt’. \| President Trump announces a roll-back of
the Obama administration’s policy of easing restrictions with Cuba at a
rally in Miami, Florida. \| The presidential Commission on Combating
Drug Addiction and the Opioid Crisis, led by New Jersey Governor Chris
Christie, holds its first meeting at the White House. \|\| **149 \|
2017-06-17**: President Trump sends a message of support via Twitter to
the families of the USS Fitzgerald (DDG-62) crew members recently killed
and injured in a collision in the Sea of Japan. \| President Trump and
First Lady Melania Trump makes their first visit to Camp David. \|
Sheriff David Clarke withdraws from his nomination for Deputy Secretary
of the Department of Homeland Security. \|\| **151 \| 2017-06-19**:
Secretary of Energy Rick Perry says he does not believe carbon dioxide
to be causing climate change. \| President Trump holds a bilateral
meeting with Panamanian President Juan Carlos Varela at the White House,
to discuss organized crime, drug trafficking and illegal migration. \|
President Trump issues a statement regarding the death of Otto Warmbier,
a prior detainee of North Korea. \| President Trump hosts the heads of
major American technology companies at the White House for the first
meeting of the American Technology Council. \|\| **152 \| 2017-06-20**:
President Trump holds a bilateral meeting with Ukrainian President Petro
Poroshenko at the White House, as new sanctions against Russia are
announced. \| The Trump administration plans to cut EPA’s budget by 31%,
firing over 1,200 staff members. \| President Trump declares on Twitter
that China’s effort to restrain the North Korean nuclear program has
failed. \| Energy Secretary Rick Perry warns of the domestic threat
posed by America’s nuclear waste. \|\| **153 \| 2017-06-21**: President
Trump visits Kirkwood Community College, Iowa, for demonstrations of new
agricultural technology. \| President Trump holds a campaign rally at
Cedar Rapids, Iowa, speaking of his plan to replace the Affordable Care
Act, and reiterating his criticism of the Democratic Party and of the
mainstream media. \| Attorney General Sessions introduces the National
Public Safety Partnership initiative, pledging federal resources to help
twelve cities combat crime. \| Vice President Pence holds the National
Summit on Crime Reduction and Public Safety at the Hyatt Regency
Bethesda hotel, featuring discussions on drug abuse and violent crime.
\|\| **154 \| 2017-06-22**: Two senior intelligence officials confirm to
Robert Mueller that the president had asked them both to publicly
announce that he had not colluded with Russia. \| President Trump hosts
many emerging technology leaders at the American Leadership in Emerging
Technology event at the White House to discuss modernizing government
technology and upcoming drone technology. \| President Trump confirms
that he made no recordings of his conversations with James Comey. \|
President Trump meets with the president of the International Olympic
Committee Thomas Bach to discuss Los Angeles’s bid to host the Summer
Olympics in 2024. \| President Trump and First Lady Melania Trump host
the first congressional picnic in the White House South Lawn, while
paying tribute to congressman Scalise. \|\| **155 \| 2017-06-23**:
President Trump nominates Woody Johnson to be the next UK ambassador. \|
President Trump signs the Department of Veterans Affairs Accountability
and Whistleblower Protection Act, making it easier to dismiss employees
for wrongdoing and adding protections for whistle-blowers. \| President
Trump cuts 400,000 of funding from Life After Hate, a non-profit group
which helps people leave the Ku Klux Klan and other white-supremacist
and Nazi organizations. \| At a Focus on the Family event in Colorado
Springs, Vice President Pence delivers a speech on religious freedom and
the pro-life movement. \|\| **156 \| 2017-06-24**: Vice President Pence
attends a Republican National Committee event in Chicago to promote his
administration’s health bill. \|\| **158 \| 2017-06-26**: The Supreme
Court reinstates, as of June 29, President Trump’s executive order
temporarily banning travelers and refugees from six Muslim-majority
countries (with the caveat that they have no direct ties to the U.S.),
in advance of a full hearing scheduled for October 2017. \| President
Trump holds a bilateral meeting and joint press conference with Indian
Prime Minister Narendra Modi at the White House. \| The White House
releases a statement warning that should Syrian President Bashar
al-Assad conduct “another mass murder attack using chemical weapons, he
and his military will pay a heavy price.” Nikki Haley states that Russia
and Iran would share any blame. \|\| **159 \| 2017-06-27**: President
Trump congratulates by telephone the new Taoiseach Leo Varadkar on
winning the Fine Gael leadership contest. \| The EPA rolls back
regulations on drinking water purity. \| Senator Mitch McConnell
postpones a vote on Trump’s initiative to repeal and replace the
Affordable Care Act. \| President Trump meets with GOP senators at the
White House concerning the pending health care bill. \|\| **160 \|
2017-06-28**: President Trump meets with the families of victims of
illegal immigrants and calls on Congress to enact new law-enforcement
legislation. \| President Trump meets with state governors and tribal
and local leaders at the White House to discuss American energy
independence. \| Vice President Pence delivers a speech at Tendon
Manufacturing in Bedford, Ohio, concerning tax cuts and employment, and
stating that the Affordable Care Act will be repealed by the end of
summer 2017. \| National Security Advisor McMaster confirms that he is
preparing a military option for Trump in respect of North Korea. \| UN
Ambassador Haley testifies to the House Committee on Foreign Affairs,
confirming that she has not discussed with President Trump Russia’s
alleged interference in the 2016 election. \| President Trump holds a
2020 election campaign fundraising event at Trump International Hotel,
Washington D.C. \| President Trump hosts the 2016 World Series Champions
Chicago Cubs at the Oval Office. \|\| **161 \| 2017-06-29**: The
president tweets about Mika Brzezinski, saying she had been “bleeding
badly from a face-lift.” \| In a speech at the Energy Department,
President Trump calls for a review of American nuclear energy policy and
for increased energy exports.\[citation needed\] \| President Trump
hosts South Korean President Moon Jae-in at the White House. \|
President Trump’s partial travel ban comes into effect at 8:00 p.m. EDT.
\|\| **162 \| 2017-06-30**: Joe Scarborough and Mika Brzezinski claim
that the White House had blackmailed with an article about their
relationship in the National Enquirer, demanding they change their news
coverage of him. \| President Trump holds a bilateral meeting and joint
press conference with South Korean President Moon Jae-in at the White
House to discuss trade and the North Korean threat in a second day of
summit talks. \| Vice President Pence and South Korean President Moon
Jae-in attend a wreath-laying ceremony at the Korean War Veterans
Memorial. \| President Trump speaks by telephone with Turkish President
Recep Tayyip Erdogan to discuss issues such as America’s support of the
YPG in Syria and the extradition of Fethullah Gulen who is accused of
masterminding the 2016 Turkish coup. \| President Trump reiterates a
prior suggestion to repeal the Affordable Care Act immediately, and
replace it later. \| President Trump signs an executive order reviving
the National Space Council. \|\| **163 \| 2017-07-01**: President Trump
attends the Celebrate Freedom Concert in Washington, paying tribute to
military veterans. \| President Trump highlights on Twitter the refusal
of 25 states to submit some or all requested voter information to the
Presidential Advisory Commission on Election Integrity. \|\| **164 \|
2017-07-02**: President Trump makes telephone calls to Chinese President
Xi Jinping and Japanese Prime Minister Shinzo Abe to discuss trade
issues and the North Korean threat. \| President Trump has telephone
conversations with Saudi Arabia’s King Salman bin Abdulaziz, Abu Dhabi’s
crown prince Sheikh Mohammed bin Zayed Al Nahyan, and Qatar’s Emir
Sheikh Tamim bin Hamad Al Thani, regarding regional peace and
counter-terrorism. \|\| **165 \| 2017-07-03**: President Trump speaks by
telephone to German Chancellor Angela Merkel discussing issues including
climate change, the Women’s Entrepreneurship Financing Initiative and
trade. \| President Trump discusses by telephone the migration crisis
and the upcoming G20 summit with Italian Prime Minister Paolo Gentiloni.
\|\| **166 \| 2017-07-04**: President Trump condemns on Twitter the
successful test launch of a North Korean ICBM potentially capable of
reaching Alaska or Australia. \| Vice President Pence attends a Fourth
of July Parade at Grandville, Michigan, with governor Rick Snyder. \|
Secretary of State Rex Tillerson says the U.S. “will never accept a
nuclear-armed North Korea”. \| The number of U.S. states refusing to
comply with President Trump’s Commission on Election Integrity is
reported to have risen to 44. \| President Trump hosts military
personnel and their families for a picnic and fireworks show at the
White House as part of Independence Day celebrations. \|\| **167 \|
2017-07-05**: President Trump, his family and advisors arrive in Warsaw,
Poland, ahead of the G20 summit. \| Ambassador Haley informs the UN
Security Council that the U.S. is prepared to deploy any of its military
options to defend itself and its allies from North Korea if other
options fail. \| Kris Kobach, vice-chairman of the Commission on
Election Integrity, confirms that 20 states have provided them with
voter information, while 14 states and the District of Columbia have
refused to do so. \|\| **168 \| 2017-07-06**: President Trump attends a
joint press conference in Warsaw with Polish President Andrzej Duda,
reaffirming the U.S. commitment to NATO and citing the “severe” options
available in respect of North Korea. \| President Trump, with the First
Lady, attends a wreath-laying ceremony at the Warsaw Uprising Monument
and delivers a speech in defense of shared democratic values, calling on
Russia to cease all destabilizing activity. \| President Trump attends
the Three Seas Initiative to discuss reduction of Central and Eastern
European nations’ dependency on Russian oil and gas imports and
increased U.S. LNG imports. \| President Trump meets with Croatian
President Kolinda Grabar-Kitarovic privately to discuss issues including
security and energy. \| President Trump arrives in Hamburg, Germany,
ahead of the G20 summit. \| President Trump meets with German Chancellor
Angela Merkel at the Hotel Atlantic to discuss issues such as trade,
climate change, global security and the threat of North Korea’s nuclear
program. \| President Trump attends the Northeast Asia Security Dinner,
discussing with South Korean President Moon Jae-in and Japanese Prime
Minister Shinzo Abe calling on China to restrain North Korea’s nuclear
ambitions. \| Vice President Pence visits the Kennedy Space Center. \|
Walter Shaub, Director of the U.S. Office of Government Ethics (OGE),
resigns effective July 19. \|\| **169 \| 2017-07-07**: President Trump
attends the G20 summit hosted by German Chancellor Angela Merkel. \|
President Trump holds a bilateral meeting with Mexican President Enrique
Pena Nieto, during which he reiterates the call for Mexico to pay for
the border wall. \| President Trump holds a bilateral meeting with
Russian President Vladimir Putin, calling for improved relations. An
undisclosed second meeting between the two occurs later in the day. \|
Secretary of State Tillerson appoints Kurt Volker Special Representative
for Ukraine Negotiations. \|\| **170 \| 2017-07-08**: President Trump
holds a bilateral meeting with British Prime Minister Theresa May,
promising to expedite a new trade deal. \| The Women Entrepreneurs
Finance Initiative is launched by First Daughter Ivanka Trump and the
World Bank whereby the U.S. commits 50 million to the fund. \| Ivanka
Trump takes President Trump’s seat at the G20 summit. \| President Trump
holds a bilateral meeting with Singaporean Prime Minister Lee Hsien
Loong, welcoming increased U.S. participation in the ASEAN-U.S. Summit,
East Asia Summit, and APEC. \| President Trump holds a bilateral meeting
with Japanese Prime Minister Shinzo Abe to discuss trade issues and
North Korea. \| President Trump holds a bilateral meeting with
Indonesian President Joko Widodo, promising to work on doing more trade
deals and business between the two countries. \| President Trump holds a
bilateral meeting with Chinese President Xi Jinping, agreeing that both
countries should put more pressure on North Korea. \| The New York Times
reports the existence of a June 9, 2016, meeting between Jared Kushner,
Paul Manafort, Donald Trump Jr. and Natalia Veselnitskaya. President
Trump says the meeting concerned adoption. \|\| **171 \| 2017-07-09**:
The New York Times reports that Donald Trump Jr. “was promised damaging
information about Hillary Clinton before agreeing to meet with a
Kremlin-connected Russian lawyer during the 2016 campaign.” \| Hours
after promoting the idea in which he stated “Putin and I discussed
forming an impenetrable cybersecurity unit so that election hacking, and
many other negative things, will be guarded and safe,” Trump says he did
not think it could actually happen. \|\| **172 \| 2017-07-10**: Vice
President Pence holds bilateral meetings with Tunisian Prime Minister
Youssef Chahed at the White House. Pence also speaks by telephone to
Macedonian Prime Minister Zoran Zaev and Greek Prime Minister Alexis
Tsipras. \|\| **173 \| 2017-07-11**: President Trump speaks by telephone
to Iraqi Prime Minister Haider al-Abadi to congratulate him on
liberation of Mosul and to stress the need for a total defeat of ISIS.
\| President Trump nominates Lewis Eisenberg to be ambassador to Italy
and San Marino. Trump also nominates Stephen B. King to be ambassador to
the Czech Republic. \|\| **174 \| 2017-07-12**: President Trump
nominates Dennis Shea, vice-chairman of the US-China Economic and
Security Review Commission, as deputy U.S. Trade Representative. \|
President Trump nominates Paul Dabbar, a JP Morgan investment banking
executive, as Under Secretary of Energy for Science. \|\| **175 \|
2017-07-13**: President Trump and First Lady Melania Trump arrive in
Paris for a two-day state visit. During the visit the president comments
that French first lady Brigitte Macron is “in such good shape”. \|
President Trump hosts a ceremony in the American embassy honoring Second
World War veterans. \| President Trump holds a bilateral meeting with
French President Emmanuel Macron at the Elysee Palace discussing
counter-terrorism and international affairs. \| Secretary of the
Interior Ryan Zinke announces the end of reviews to monument
modifications in Craters of the Moon National Monument in Idaho and in
Washington Hanford Reach National Monument. \|\| **176 \| 2017-07-14**:
President Trump and First Lady Melania Trump attend a Bastille Day
military parade in Paris with French President Emmanuel Macron. \|
President Trump attends the U.S. Women’s Open at Trump National Golf
Club at Bedminster, New Jersey. \| Vice President Pence, with Canadian
Prime Minister Justin Trudeau, attends a U.S. governors’ meeting in
Rhode Island for talks on health care and NAFTA. \|\| **179 \|
2017-07-17**: President Trump launches “Made in America Week” at the
White House by showcasing products made in all 50 states. \|\| **180 \|
2017-07-18**: The US military is reported to have rented 2.4 million
dollars worth of space at the Trump Tower. \| Vice President Pence
attends the Retail Advocates Summit organized by the National Retail
Federation promoting tax reform. \| President Trump nominates former
Utah governor Jon Huntsman Jr. as ambassador to Russia. \|\| **181 \|
2017-07-19**: The president says that he would not have hired Jeff
Sessions as the Attorney General if he had known he would recuse himself
from the Russia investigation. \| President Trump attends the first
meeting of the Commission on Election Integrity chaired by Vice
President Pence, calling for a full investigation of the electoral
process. \| President Trump has a luncheon with Republican senators in
the White House, calling on them to work on repealing and replacing the
Affordable Care Act. \| President Trump hosts a “Made in America”
roundtable event at the White House with CEOs of American companies,
calling for a crackdown on counterfeit goods from overseas. \| President
Trump nominates Mark Esper as Secretary of the Army and Robert Wilkie as
Undersecretary of Defense for Personnel and Readiness. \|\| **182 \|
2017-07-20**: President Trump meets with his national security team at
the Pentagon to discuss troop levels in Afghanistan and the fight
against the Islamic State of Iraq and the Levant. The meeting is
reportedly contentious and became the moment when Rex Tillerson decided
to resign his position. \| President Trump announces that 500 million
will be made available for the production of domestic glass
pharmaceutical packaging to representatives from Merck, Pfizer and
Corning. \|\| **183 \| 2017-07-21**: President Trump signs an executive
ordering a review of the U.S. defense industrial base and military
supply chains. \| President Trump appoints Anthony Scaramucci his new
White House Communications Director. \| White House Press Secretary Sean
Spicer resigns, effective at the end of August. \| President Trump
honors surviving members of the USS USS Arizona (BB-39) during a visit
to the White House. \| H. R. McMaster dismisses Rich Higgins from the
National Security Council following exposure of a memorandum, authored
by Higgins, outlining a theory that the media, bankers, Islamists,
cultural Marxists, and both political parties are plotting to destroy
Trump’s presidency. \|\| **184 \| 2017-07-22**: In a phone call to Ryan
Lizza, the newly appointed Communications Director Anthony Scaramucci
calls Chief of Staff Reince Priebus a “fucking paranoid schizophrenic”
and notes that unlike Steve Bannon he is “not trying to suck my own
cock”. \| President Trump commissions the aircraft carrier USS Gerald R.
Ford (CVN-78) at Naval Station Norfolk, Virginia. \|\| **186 \|
2017-07-24**: President Trump calls AG Jeff Sessions “beleagured”. \|
The president calls Adam Schiff “sleazy” and “totally biased”. \|
President Trump meets with families described by the White House as
“victims” of the Affordable Care Act, holding a press conference urging
Senators to repeal and replace it. \| President Trump attends the 2017
National Scout Jamboree at Glen Jean, West Virginia, praising the
organization and its values. The Boy Scouts’ chief executive issues a
formal apology on July 27 for the speech’s “political rhetoric”. \|
Jared Kushner issues a statement at the White House denying all
collusion with Russian officials, following a meeting with the Senate
Intelligence Committee. \|\| **187 \| 2017-07-25**: President Trump
holds a bilateral meeting and joint press conference with Lebanese Prime
Minister Saad Hariri at the White House to discuss the humanitarian
problem in Syria, Hezbollah, and anti-terrorism. \| President Trump
promises more help to veterans during a private gathering of local
veteran organizations at Struthers, Ohio, as part of American Heroes
Week. \| President Trump holds a campaign style rally in Youngstown,
Ohio, touting the successes of his administration. \|\| **188 \|
2017-07-26**: President Trump says, “The United States Government will
not accept or allow … transgender individuals to serve in any capacity
in the U.S. Military,” citing disruptions and medical costs. \| The
Trump administration begins to roll back a regulation expanding overtime
pay to 4.2 million workers. \| President Trump hosts the American Legion
Boys Nation and the American Legion Auxiliary Girls Nation at the White
House. \| President Trump donates his second-quarter salary to the
Department of Education. \| President Trump announces a 10 billion
investment by Chinese company Foxconn to build a manufacturing facility
in Wisconsin, with a 3 billion subsidy. \| President Trump nominates
Kansas Governor Sam Brownback as ambassador of the Office of
International Religious Freedom. \| The Justice Department files a legal
brief on behalf of the United States arguing that the 1964 Civil Rights
Act does not prohibit discrimination based on sexual orientation or,
implicitly, gender identity. \|\| **189 \| 2017-07-27**: Chief of Staff
Reince Priebus resigns. \| President Trump awards the Medal of Valor to
five first responders for their actions in the shooting at a
congressional baseball practice. \| President Trump nominates six
diplomatic ambassadors: John R. Bass for Afghanistan; Michael James
Dodman for Mauritania; Peter Hoekstra for the Netherlands; Daniel
Kritenbrink for Vietnam; Justin Hicks Siberell for Bahrain; and Michele
Jeanne Sison for Haiti. \| George Papadopoulos is arrested upon arrival
at Washington Dulles International Airport. \|\| **190 \| 2017-07-28**:
President Trump appoints John F. Kelly as White House Chief of Staff,
replacing Reince Priebus. \| President Trump addresses law enforcement
officers at Suffolk County Community College calling for increased
border security and a crackdown on transnational crime. \|\| **191 \|
2017-07-29**: President Trump describes Republican Senators as looking
like “fools” following a 49-51 vote against his initiative to repeal the
Affordable Care Act. \| President Trump threatens to end healthcare
cost-sharing subsidies to insurers and lawmakers. \|\| **193 \|
2017-07-31**: John Kelly is sworn in as the White House Chief of Staff.
\| Anthony Scaramucci is removed as the White House Communications
Director 16 days after taking office, following crude remarks made in an
interview to The New Yorker. \| Treasury Secretary Steve Mnuchin
announces sanctions against Venezuelan President Nicolas Maduro. \|
President Trump awards the Medal of Honor at the White House to James
McCloughan, a former army medic who served during the Vietnam War. \|
Press Secretary Sanders states her belief that President Trump was
“joking”, when asked about allegations that he promoted police brutality
at a speech to law enforcement officers at Suffolk County Community
College on July 28. \|\| **194 \| 2017-08-01**: The Trump re-election
campaign chooses a white nationalist as an elector in the next
presidential election. \| President Trump, as part of ‘American Dream
Week’, holds a small business owners event at the White House touting
American growth. \|\| **195 \| 2017-08-02**: President Trump signs a
Congressional bill (H.R.3364) limiting his ability to ease sanctions
against Russia, despite describing the bill as “flawed” and
“unconstitutional”. \| Secretary of State Rex Tillerson is reported as
having not spent 60 million dollars available to combat Russian and
Chinese disinformation. \| President Trump’s campaign team hands over
20,000 pages of documents to the Senate Judiciary Committee in relation
to the ongoing investigations concerning Russian collusion with Trump’s
election campaign team. \| The president is reported to have complained
about NATO allies and asked how the US could exploit Afghanistan’s
mineral wealth. \| Sam Clovis, the president’s nominee to be the leading
scientist at the United States Department of Agriculture, is reported to
have run a blog calling progressives “race traders and race ‘traitors.’”
\| President Trump introduces a new bill entitled “The Raise Act” which
proposes to replace the current permanent employment-immigration
framework with a merit- and skill-based immigration system. \| Ezra
Cohen-Watnick, leader of the NSC’s Intelligence directorate, is removed
from his position. \|\| **196 \| 2017-08-03**: President Trump hosts a
Veterans Affairs Telehealth Services event at the White House unveiling
a new service for veterans allowing patients to schedule health care
appointments from their smartphones or home computers. \| President
Trump attends a rally at Huntington, West Virginia, where Governor Jim
Justice announces his switch from the Democrats to the Republicans. \|\|
**197 \| 2017-08-04**: President Trump and Vice President Pence visit
the FEMA headquarters to review preparations and emergency responses for
the upcoming hurricane season. \| President Trump discusses in a phone
conversation with French President Emmanuel Macron increased cooperation
in Iraq, Syria and countering Iranian influence in the Middle East. \|
Attorney General Jeff Sessions announces a crackdown on individuals who
leak classified or sensitive national security information, as well as a
review of the way in which journalists are subpoenaed. \|\| **199 \|
2017-08-06**: President Trump has a phone conversation with South Korean
President Moon Jae-in, discussing ways to stop the North Korean nuclear
program. \| Secretary of State Tillerson attends the ASEAN summit in
Manila to push its members and partners to apply more pressure on North
Korea to halt its nuclear program. \|\| **200 \| 2017-08-07**: Secretary
of State Tillerson meets with Philippines President Rodrigo Duterte to
discuss global terrorism, economic cooperation and the security
situation in Marawi. \|\| **201 \| 2017-08-08**: President Trump warns
North Korea of “fire and fury” following threats to retaliate against
new United Nations sanctions. \| Secretary of State Tillerson has
discussions with Thai Prime Minister Prayut Chan-o-cha and Foreign
Minister Don Pramudwinai on regional security and trade in Bangkok. \|
Secretary of State Tillerson meets with Malaysian Prime Minister Najib
Razak in Kuala Lumpur to discuss international relations and trade. \|
President Trump holds a press briefing at Bedminster, New Jersey,
calling for tougher enforcement to combat the opioid problem in the
country. \|\| **202 \| 2017-08-09**: President Trump draws attention on
Twitter to the “power” of the U.S. nuclear arsenal. \| President Trump
speaks by telephone with Senator Mitch McConnell; he complains that
McConnell is not protecting him from the Senate’s Russia inquiry. \|
Defense Secretary Mattis warns North Korea that an attack on the U.S. or
its allies will prompt “the destruction of its people”. \|\| **203 \|
2017-08-10**: President Trump talks to reporters about his “fire and
fury” warning, stating that “if anything, maybe that statement wasn’t
tough enough.” \| President Trump declares that the opioid crisis is a
national emergency that will need a lot of attention and money to
combat. \| President Trump states that he is “very thankful” that
Vladimir Putin ordered removal of 755 diplomatic posts from Russia,
reducing the U.S. payroll. \|\| **204 \| 2017-08-11**: President Trump
states on Twitter that America’s military capabilities against North
Korea are “locked and loaded”. \| President Trump does not rule out the
possibility of military action against President Nicolas Maduro in
response to the ongoing Venezuelan political crisis. \| President Trump
retracts his statement thanking Vladimir Putin on August 10 and states
that his original comment was sarcastic. \| President Trump holds a
workforce and apprenticeship discussion with Secretary of Education
Betsy DeVos and Secretary of Labor Alex Acosta on ways to help Americans
access affordable education and training which, according to a White
spokesperson, will equip them with relevant skills to help them secure
good jobs. \|\| **205 \| 2017-08-12**: President Trump speaks to Chinese
President Xi Jinping, who requests restraint concerning tensions in the
Korean peninsula. \| President Trump signs the Veterans Affairs Choice
and Quality Employment Act, which will provide veterans private medical
care using government funds for the next six months. \| President Trump
condemns the violence from all sides at a far-right rally at
Charlottesville, Virginia, and calls for law and order to be restored.
He notably opted to omit any mention of the murdered counter-protester
Heather Heyer in his address; he also chose to not single out or
specifically condemn the alt-right protester James Alex Fields for that
murder, and to not condemn the neo-Nazi movement. Trump faced bipartisan
criticism for these omissions. \|\| **206 \| 2017-08-13**: Vice
President Pence arrives in Colombia meeting with Colombian President
Juan Manuel Santos to cover trade, business and investment opportunities
in both countries. \| Speaking in a press conference in Cartagena, Vice
President Pence condemns neo-Nazism and the Ku Klux Klan, and rejects
allegations that President Trump had failed to censure white
supremacists explicitly in his previous remarks, saying the media has
overblown the issue. \| National Security Advisor McMaster denounces a
fatal vehicular attack on counterprotestors in Charlottesville on August
12 as “terrorism”. \|\| **207 \| 2017-08-14**: President Trump again
condemns the violence that took place at the rally in Charlottesville,
Virginia. \| President Trump signs an executive order authorizing U.S.
Trade Representative Robert Lighthizer to begin investigations into
Chinese trade practices that harm American businesses, with particular
focus on intellectual property and advanced technology. \| President
Trump speaks by phone to Japanese Prime Minister Shinzo Abe on finding
ways to prevent North Korea launching ballistic missiles at Guam across
Japanese territory. \| Attorney General Sessions decries the August 12
Charlottesville vehicle attack as “domestic terrorism”. \| The CEOs of
Merck, Intel and Under Armour resign from the American Manufacturing
Council in protest at President Trump’s response to the Charlottesville
rally. \|\| **208 \| 2017-08-15**: President Trump signs an executive
order calling for federal departments to speed up the permits process
for construction of transportation, water and other infrastructure
projects. He revokes regulations intended to manage and prevent
flooding. \| President Trump holds a press conference at which he goes
“off teleprompter” and reverts to his earlier apportioning of blame in
Charlottesville, apparently equally, to both sides. At this same news
conference he voices his personal support of the rationale of the
Alt-right’s claim that General Lee was a historical figure of similar
historical importance to Lincoln, Washington and Jefferson, and that he
therefore supported the Alt-Right’s rationale for protesting against the
removal of the Charlottesville statue of General Lee. \| Scott Paul,
president of the Alliance for American Manufacturing, and Richard
Trumka, president of AFL-CIO, resign from the American Manufacturing
Council. President Trump describes the resignees as “grandstanders”. \|
Vice President Pence holds meetings with Argentinian President Mauricio
Macri in Buenos Aires, focused on strengthening business ties between
their two countries. \|\| **209 \| 2017-08-16**: President Trump
appoints Hope Hicks as interim White House Communications Director,
replacing Scaramucci. \| After the fallout from Trump’s handling of the
Charlottesville protest, numerous members of President Trump’s American
Manufacturing Council announce their intention to resign from the
Council. President Trump announces the dissolution of the Council and
also of the Strategic and Policy Forum following the resignations of
Inge Thulin, CEO of 3M, and Campbell’s Soup Company CEO Denise Morrison.
\| President Trump signs a veterans’ education bill to provide college
assistance for military veterans and increase these payments if they
complete science, technology and engineering courses. \| In Santiago,
Chile, Vice President Pence has a meeting with Chilean President
Michelle Bachelet to build business ties between both countries and to
call for Chile to break its diplomatic ties with North Korea. \|\| **210
\| 2017-08-17**: President Trump condemns a fatal terrorist attack in
Barcelona and offers Spain the full support of the United States. \|
President Trump scraps plans initiated by Executive Order on July 19 for
the setup of an Advisory Council on Infrastructure. \| President Trump
holds meetings with the Small Business Administration chief Linda
McMahon on finding ways to help small business who have difficulty
getting loans and finding the right workers. \| The White House
announces a deal whereby the U.S. can resume exporting pork to
Argentina, for the first time since 1992. \| Vice President Pence has
meetings with Panamanian President Juan Carlos Varela focusing on
commercial and security ties, as well as tackling drug trafficking,
illegal migration and money laundering, culminating with a tour of the
Panama Canal. \|\| **211 \| 2017-08-18**: President Trump directs that
the U.S. Cyber Command (USCYBERCOM) be elevated to the status of a
Unified Combatant Command (UCC). \| The White House announces that Chief
Strategist Steve Bannon has left his position “by mutual agreement”. \|
Numerous presidential advisors resign, among them pastor A. R. Bernard,
Microsoft president Brad Smith, Mozilla chairwoman Mitchell Baker,
Comcast executive vice president David L. Cohen and investor Carl Icahn.
\| 17 members of the White House arts and humanities advisory panel
resign, delivering an open letter condemning President Trump for his
“support of the hate groups and terrorists who killed and injured fellow
Americans in Charlottesville”. \| President Trump signs the Global War
on Terrorism War Memorial Act, authorizing construction of a memorial to
U.S. servicemen who participated in the global war on terrorism. \|
President Trump holds a conference at Camp David with his national
security team to discuss military options in Afghanistan. \|\| **212 \|
2017-08-19**: President Trump praises 30,000 protestors against a
right-wing Free Speech Rally in Boston for “speaking out against bigotry
and hate”, and criticizes “anti-police agitators”. \|\| **214 \|
2017-08-21**: President Trump gives an address at Fort Myer, Virginia,
reaffirming military commitment to Afghanistan and disavowing Pakistan’s
sheltering the Taliban. \| President Trump swears in New York Jets owner
Woody Johnson, as Ambassador to the UK. \| Seven members of the National
Infrastructure Advisory Council send a letter of resignation to the
White House, asserting that President Trump is paying “insufficient
attention” to cyber-security threats to the nation’s infrastructure.
\|\| **215 \| 2017-08-22**: President Trump tours a U.S. Customs +
Border Protection facility in Yuma, Arizona, meeting with Marines and
border patrol agents, and inspecting border security technology and
equipment. \| President Trump holds a political rally in Phoenix,
Arizona, reiterating his condemnation of the violence at
Charlottesville, accusing the media of distorting coverage of his
response, while commenting on his administration’s achievements. He
announces a willingness to shut down the federal government if Congress
refuses to allocate funds for his Mexican wall policy. \| U.S.
ambassador to the United Nations, Nikki Haley, in a meeting with the
International Atomic Energy Agency officials at Vienna, Austria, calls
for the nuclear watchdog to inspect Iranian military sites to verify
compliance with the 2015 nuclear deal. \|\| **216 \| 2017-08-23**:
President Trump in a speech to the American Legion in Reno, Nevada,
calls for Americans to unite and reiterates the themes of his campaign,
including crime, terrorism, manufacturing and infrastructure. \| The
White House instructs the Pentagon to develop a policy on transgender
service members, notably considering their individual combat
deployability, and curtailing subsidies for medical treatment or
operations. \| President Trump signs the Veterans Appeals Improvement
and Modernization bill intended to allow better options and transparency
for veterans when appealing benefit claims. \| Vice President Pence
mentions in a speech to South Florida Venezuelans that the U.S. will use
the full measure of its economic and diplomatic power to end political
repression in Venezuela. \| State Department science envoy Daniel Kammen
resigns in protest at President Trump’s response to the violence at
Charlottesville on August 12. \|\| **217 \| 2017-08-24**: President
Trump speaks by telephone with Texas Governor Greg Abbott and Louisiana
Governor John Bel Edwards regarding Hurricane Harvey, and pledges
federal aid. \| Secretary of Interior Zinke sends a draft report to
President Trump on his findings and recommendations on national
monuments. \|\| **218 \| 2017-08-25**: President Trump issues
Presidential Memorandum for the Secretary of Defense and the Secretary
of Homeland Security. \| President Trump monitors the situation with
Hurricane Harvey from Camp David, Maryland, and signs a disaster
proclamation that will guarantee federal aid to the region affected. \|
President Trump issues a presidential pardon for Sheriff Joe Arpaio who
was convicted of criminal contempt in a case involving his department’s
racial profiling policy, praising Arpaio’s life work in protecting the
public from crime and illegal immigration. \| President Trump signs an
executive order barring the U.S. financial system from any dealings in
new bonds and stocks issued by the Venezuelan government and its state
oil company. \| Sebastian Gorka leaves his position as Deputy Assistant
to the President. \| U.S. ambassador to the UN Nikki Haley criticizes
the United Nations Interim Force in Lebanon commander, Major General
Michael Beary, for not tackling the flow of illegal arms to
Hezbollah-dominated Southern Lebanon but does not provide proof to back
up her claims. \|\| **221 \| 2017-08-28**: President Trump holds a
bilateral meeting and joint press conference with Finnish President
Sauli Niinisto at the White House to discuss terrorism, Afghanistan,
Russia, the Baltic Sea and the Arctic. \| President Trump signs an
executive order to restore the flow of surplus military equipment to
local and state police agencies. \|\| **222 \| 2017-08-29**: President
Trump and First Lady Melania Trump arrive in Corpus Christi, Texas, to
meet with Texas Governor Greg Abbott, Texas Senators Ted Cruz and John
Cornyn, and FEMA Administrator Brock Long to discuss Hurricane Harvey.
Trump later travels to the Texas Department of Public Safety’s Emergency
Operations Center in Austin, Texas, for further briefing. \| President
Trump said in a statement that “all options are on the table”, after
North Korea conducts \| a mid-range missile launch which flies over
Northern Japan. \| President Trump, in a phone call with Singaporean
Prime Minister Lee Hsien Loong, accepts Singapore’s offer of the use of
its Texas-based \| Chinook helicopters to assist in Hurricane Harvey
disaster-relief efforts. \|\| **223 \| 2017-08-30**: President Trump
gives a speech in Springfield, Missouri, calling for tax reform. \|
President Trump posts on Twitter that the U.S. has been paying North
Korea “extortion money” and that “talking is not the answer”. \| Vice
President Pence in a speech to the West Virginia Chamber of Commerce’s
annual business summit called for tax overhaul reform, describing the
current tax system as deleterious to employment and entrepreneurialism.
\|\| **224 \| 2017-08-31**: The Trump administration announces a cut of
90% to the Affordable Care Act’s advertising budget. \| Vice President
Pence arrives in Corpus Christi, Texas, to survey the damage caused by
Hurricane Harvey and meet with people affected by the storm. \| Energy
Secretary Rick Perry authorizes the Strategic Petroleum Reserve to
release oil supplies to combat fuel price spikes, due to the shutdown of
oil refineries in Texas which were affected by Hurricane Harvey. \|
President Trump will donate 1 million of his own funds to recovery
efforts in Texas according to the White House. \| Defense Secretary
James Mattis signs orders to deploy additional troops to Afghanistan as
part of the Trump’s new military strategy in the region. \|\| **225 \|
2017-09-01**: President Trump signs a declaration designating September
3, 2017, as a “Day of Prayer” for victims of Hurricane Harvey. \| The
Department of Justice in a court filing makes its first official
confirmation that neither it nor the FBI have evidence to support
President Trump’s allegation that then-President Obama wiretapped Trump
Tower in New York. \| President Trump nominates Richard Grenell as
United States Ambassador to Germany. If confirmed by the Senate, Grenell
would be the Trump administration’s first openly gay appointee. \|\|
**226 \| 2017-09-02**: President Trump and First Lady Melania meet with
and help to distribute food and supplies to victims of Hurricane Harvey
at the NRG Center in Houston, Texas. \| President Trump meets and thanks
members of the Louisiana National Guard and the Cajun Navy at Lake
Charles, Louisiana, who helped rescued people from the Hurricane Harvey
floods. \| Press Secretary Sanders denies a report that Director of Oval
Office Operations Keith Schiller intends to resign. \|\| **227 \|
2017-09-03**: Following the latest North Korean nuclear test, President
Trump and Treasury Secretary Mnuchin raise the possibility of ceasing
trade with countries trading with North Korea. \| Defense Secretary
Mattis publicly states: “We are not looking to the total annihilation of
a country, namely North Korea, but \[…\] we have many options to do so”.
\|\| **228 \| 2017-09-04**: In an emergency UN Security Council meeting,
Ambassador Nikki Haley says the U.S. will present a new sanctions
resolution to punish North Korea for the latest nuclear test. \|\| **229
\| 2017-09-05**: Attorney General Sessions announces at a special
briefing that, at President Trump’s order, the Department of Homeland
Security will immediately cease to accept applications to the Deferred
Action for Childhood Arrivals program. It is confirmed that current DACA
recipients will be unaffected until March 5, 2018. Trump shortly
thereafter calls on Congress to “legalize DACA”. \| In response to the
North Korea threat, President Trump states that he will allow South
Korea and Japan to purchase additional sophisticated military equipment
from the U.S. \| In a phone conversation, President Trump and Australian
Prime Minister Malcolm Turnbull agree on the need for the international
community to exert maximum diplomatic and economic pressure on North
Korea. \| President Trump holds a tax summit at the White House with his
top advisors and Republican leaders to discuss reforming the U.S. tax
system. \| The head of the Hispanic Chamber of Commerce, Javier
Palomarez, resigns from Trump’s National Diversity Council in protest at
the DACA announcement. \|\| **230 \| 2017-09-06**: President Trump meets
with Congressional leaders from both parties to discuss disaster relief
for the aftermath of Hurricane Harvey, raising the debt ceiling to
prevent a government shutdown and federal spending legislation. \|
President Trump declares emergencies in Florida, Puerto Rico and the
U.S. Virgin Islands for Hurricane Irma, instructing the Department of
Homeland Security and the Federal Emergency Management Agency to
coordinate disaster relief efforts. \| At an oil refinery at Mandan,
North Dakota, President Trump speaks to a friendly crowd calling for the
restoration of American competitive edge, using tax cuts and reform.
\|\| **231 \| 2017-09-07**: President Trump holds a bilateral meeting
with Emir Sabah Al-Ahmad Al-Jaber Al-Sabah of Kuwait at the White House
regarding developing economic, financial, and commercial ties between
both countries. \| President Trump talks to officials led by Governor
Andrew Cuomo of New York and Governor Chris Christie of New Jersey about
the Gateway Tunnel project as part of the administration’s avowed
priority on modernizing the nation’s infrastructure. \| President Trump
approves South Carolina’s request for an emergency declaration in the
state in preparation for Hurricane Irma. \| Secretary of Education Betsy
DeVos confirms that there will be rollback of the college campus sexual
assault directives or Title IX guidelines put in place during the Obama
administration, asserting that the system has failed sexual assault
survivors and those wrongly accused. \| The Justice Department files a
legal brief in the Supreme Court, arguing for a constitutional right of
businesses to discriminate on the basis of sexual orientation and,
implicitly, gender identity. \|\| **232 \| 2017-09-08**: President Trump
speaks by phone to Saudi Arabia’s Crown Prince Mohammed bin Salman Al
Saud, the United Arab Emirate’s Crown Prince Mohammed bin Zayed Al
Nahyan and Qatar’s Emir Tamim bin Hamad Al Thani concerning regional
stability. \| President Trump signs a disaster 15.25 billion relief bill
for Hurricane Harvey and Irma, which includes raising the federal debt
ceiling for the next three months. \|\| **233 \| 2017-09-09**: At Camp
David, President Trump and his cabinet hold team-building sessions,
hurricane briefings and strategy meetings, with special focus on
Hurricane Irma and tax reform. \| President Trump speaks by phone to
Turkish President Recep Tayyip Erdogan, agreeing to further strengthen
bilateral relations and increase stability in the Middle East. \|\|
**234 \| 2017-09-10**: President Trump approves a disaster declaration
for Florida which will authorize federal funding for areas affected by
Hurricane Irma and will reimburse local and the state authorities for
costs of response and recovery. \| During a visit to FEMA headquarters
in Washington, Vice President Pence made assurances that the federal
assistance was on its way to help the people of Florida recover from the
effects of Hurricane Irma. \|\| **235 \| 2017-09-11**: President Trump
and First Lady Melania Trump lay a wreath at the September 11 Memorial
at the Pentagon, and later pay tribute to the nearly three thousand
Americans killed that day, pledging to continue to confront radical
Islamic terrorism. \|\| **236 \| 2017-09-12**: President Trump holds a
bilateral meeting with Malaysian Prime Minister Najib Razak at the White
House focusing on trade, Islamic terrorism and Malaysian interest in
Trump’s infrastructure program. \| President Trump holds a dinner with a
group of bipartisan senators at the White House to discuss tax reform.
\| It is reported that Trump’s team has for the first time submitted
documents to Special Counsel Robert Mueller. \|\| **237 \| 2017-09-13**:
President Trump declares September 15 - October 15 as National Hispanic
Heritage Month. \| President Trump hosts a bipartisan dinner at the
White House to discuss tax reform and find ways to come up with
legislation dealing with DACA recipients. \| Daniel Craig withdraws from
Trump’s nomination to be deputy administrator of FEMA. \|\| **238 \|
2017-09-14**: President Trump and Vice President Pence travel to Fort
Myers, Florida, to be briefed on Hurricane Irma relief efforts with
state and federal leaders, while praising first responders and local
officials for their work and lives saved. \| President Trump, Vice
President Pence and First Lady Melania Trump help to distribute food and
supplies to survivors of Hurricane Irma at Naples, Florida. \| President
Trump reiterates his argument that both sides at the rally in
Charlottesville were at fault, prior to signing a Congressional
resolution condemning White nationalists, White supremacists, the Ku
Klux Klan, neo-Nazis and other hate groups. \| President Trump and First
Lady Melania Trump host a White House dinner reception for the White
House Historical Association whose mission to protect, preserve, and
provide public access to the history of the White House. \|\| **239 \|
2017-09-15**: Nikki Haley and Secretary of Defense James Mattis give
statements on North Korea, Mattis saying the U.S. has options to use
against North Korea if sanctions do not work. \| Vice President Pence’s
press secretary Marc Lotter announces his departure from the White
House. \| President Trump in a phone call to Jewish leaders and rabbis
reaffirms the administration’s strong support for Israel and honors the
upcoming celebration of High Holy Days such as Yom Kippur and Rosh
Hashana. \| President Trump and First Lady Melania Trump meet with
military families and watch an air show at Andrew Airforce Base, with
the President honoring the resolve of the nation’s Air Force and warning
foes and international terrorist groups that the U.S. military would
respond to any threats. \| Defense Secretary Jim Mattis meets with his
Mexican counterparts in the Mexico City to reinforce military ties and
take part in commemorations of Mexico’s independence day. \|\| **241 \|
2017-09-17**: President Trump, in a phone call to South Korean President
Moon Jae-in, pledges to impose stronger sanctions on North Korea to
counter its missile and nuclear programs. \|\| **242 \| 2017-09-18**:
President Trump attends the “Reforming the United Nations: Management,
Security, and Development” forum at the United Nations, calling on
members to pay more for joint projects such as peacekeeping missions. \|
President Trump holds a bilateral meeting with Israeli Prime Minister
Benjamin Netanyahu to discuss a possible future peace deal between the
Israelis and Palestinians, and alleged Iranian aggression in the Middle
East. \| President Trump holds a bilateral meeting with French President
Emmanuel Macron to discuss the Paris Climate Change Agreement and the
Iran nuclear deal. \| President Trump has dinner meeting with Latin
American leaders such as Brazilian President Michel Temer, Colombian
President Juan Manuel Santos, Panamanian President Juan Carlos Varela
and Argentinian Vice President Gabriela Michetti to discuss the
restoration of democracy in Venezuela. \| Vice President Pence appoints
Alyssa Farah as his press secretary, replacing Marc Lotter. \|\| **243
\| 2017-09-19**: In his maiden speech to the United Nations General
Assembly, President Trump announces that if Kim Jong-un, dubbed “Rocket
Man”, forces the United States to defend itself or its allies, the
United States will “totally destroy” North Korea. Trump also indicates
the possibility of further action against Venezuelan President Maduro’s
regime, denounces Iran as a “corrupt dictatorship”, and describes the
Iranian nuclear deal as an “embarrassment”. He calls on the UN to work
together to solve such issues. \| President Trump attends a lunch
meeting hosted by UN Secretary General Antonio Guterres, seated with the
leaders of Japan, South Korea, Turkey, and others.\[note 1\] \|
President Trump holds a bilateral meeting with Qatari Emir Tamim bin
Hamad Al Thani to discuss solving the dispute between Qatar and the Arab
states. \|\| **244 \| 2017-09-20**: President Trump holds a bilateral
meeting with King Abdullah II of Jordan to discuss fighting terrorism in
the Middle East and praises Jordan for taking refugees from Syria. \|
President Trump holds a bilateral meeting with Palestinian President
Mahmoud Abbas, promises to work on a peace deal between the Israelis and
Palestinians. \| President Trump hosts a working lunch with African
Union leader Alpha Conde and leaders from Nigeria, Cote d’Ivoire,
Ethiopia, Ghana, Guinea, Namibia, Senegal, Uganda and South Africa,
discussing economic opportunities in the African continent and the
security situation South Sudan and Congo. \| President Trump holds a
bilateral meeting with British Prime Minister Theresa May to discuss
trade, North Korea, and Iran. \| President Trump holds a bilateral
meeting with Egyptian President Abdel Fattah el-Sisi and mentions he was
considering the resumption of the foreign military aid to Egypt which
was frozen over concerns of its human rights record. \| Long-time aide
and confidant to President Trump Keith Schiller leaves his position as
the Director of Oval Office Operations. \|\| **245 \| 2017-09-21**:
President Trump holds a bilateral meeting with Afghan President Ashraf
Ghani to discuss the Afghanistan war strategy in combating Islamist
terrorists. \| President Trump holds a bilateral meeting with Ukraine
President Petro Poroshenko to discuss issues such as trade between both
countries and the security situation in Ukraine. \| President Trump
signs an executive order targeting individuals and companies trading
with North Korea, including sanctions on foreign banks. \| President
Trump holds a bilateral meeting with South Korean President Moon Jae-in
to discuss recent provocations by North Korea. \| President Trump holds
a bilateral meeting with Japanese Prime Minister Shinzo Abe and agree on
their support for UN sanctions on North Korea. \| President Trump holds
a bilateral meeting with Turkish President Recep Tayyip Erdogan to
discuss regional developments such as the Russian sale of S-400 missile
system to Turkey and Northern Iraqi Kurdish independence referendum. \|
The White House instructs the Environment Protection Agency to begin
ordering employees to attend anti-leaking class to reinforce their
compliance with laws and rules against leaking classified or sensitive
government information to the media or outside parties. \|\| **246 \|
2017-09-22**: President Trump attends a political rally in Huntsville,
Alabama, in support of the election campaign of Luther Strange. \| Vice
President Pence discusses the administration’s efforts in tax reform in
front of a crowd at the Flagship Enterprise Center, Anderson, Indiana.
\| Secretary of Education Betsy DeVos rescinds the previous
administration’s guidelines for colleges and universities in handling
sexual misconduct claims under Title IX and introduced new guidelines in
reporting these claims. \|\| **247 \| 2017-09-23**: In response to a
tweet by President Trump withdrawing an invitation to NBA player Stephen
Curry to visit the White House, the entire Golden State Warrior team
says it will forego the traditional championship team Oval office visit.
\|\| **248 \| 2017-09-24**: President Trump signs a new presidential
proclamation introducing new travel restrictions on countries North
Korea, Venezuela, and Chad along with countries Somalia, Yemen, Syria,
Libya and Iran listed under Executive Order 13780. \|\| **249 \|
2017-09-25**: President Trump signs a presidential memorandum directing
the Department of Education to allocate at least 200 million per year in
grant funds to the study of science and engineering. \| President Trump
hosts a dinner with the several conservative grassroot leaders at the
White House to discuss tax reform. \| Vice President Pence visits the
Marshall Space Flight Center in Huntsville, Alabama. \| Vice President
Pence attends a campaign rally in support of Luther Strange in a special
Republican runoff election. \|\| **250 \| 2017-09-26**: President Trump
meets with a bipartisan group of members of House Ways and Means
Committee to discuss tax reform and tax cuts. \| President Trump attends
a briefing on damage caused Hurricane Maria on the island of Puerto
Rico, promising to visit the island and send more aid. \| President
Trump holds a bilateral meeting and joint press conference with Spanish
Prime Minister Mariano Rajoy at the White House to discuss both
countries commitments in combating terrorism, the situations with North
Korea and Venezuela and their opposition to Catalonia’s independence
from Spain. \| President Trump headlines an RNC fundraiser in New York
City. \| A third attempt at a Senate vote on President Trump’s
initiative to repeal the Affordable Care Act is abandoned. \| Defense
Secretary James Mattis meets with Indian Defence Minister Nirmala
Sitharaman in New Delhi to discuss defense, trade and technology. \|
Chuck Rosenberg, acting administrator of the Drug Enforcement
Administration, announces his resignation effective October 1. \|\|
**251 \| 2017-09-27**: President Trump discusses his plan to reform the
tax system in Indianapolis, Indiana calling for the sweeping tax cuts,
reducing the personal income tax brackets and corporate taxes and
eliminating the estate tax. \| Defense Secretary James Mattis arrives in
Kabul, Afghanistan with NATO Secretary General Jens Stoltenberg to meet
with Afghan President Ashraf Ghani and discuss the security situation in
the country and combating the Taliban. \|\| **252 \| 2017-09-28**:
President Trump attends the celebration for the 70th anniversary of the
National Security Council at the Eisenhower Executive Office Building.
\| President Trump meets Chinese Vice-Premier Liu Yandong to discuss
Trump’s visit to China and international cooperation between both
countries. \| Vice President Pence speaks to a crowd in a factory at
Auburn Hills, Michigan touting the administration’s tax reform proposal.
\| President Trump has picked Texas Supreme Court Justice Don Willett
and former Texas Solicitor General James Ho as nominees for the Fifth
Circuit Court of Appeals. \| It is reported that the White House is
conducting an investigation into the use of private email accounts by
senior members of the administration, including Jared Kushner, for
official business. \|\| **253 \| 2017-09-29**: President Trump speaks to
the National Association of Manufacturers about the economy and his tax
plan. \| Secretary of Health and Human Services Tom Price resigns from
his position after reports of criticism over extensive use of private
jets, with President Trump naming Don J. Wright, a deputy assistant
secretary of health, to serve as acting secretary. \|\| **254 \|
2017-09-30**: Secretary of State Rex Tillerson meets with Chinese
President Xi Jinping in Beijing, China to discuss bilateral relations
between both countries and President Trump’s upcoming visit to China in
November. \|\| **255 \| 2017-10-01**: The deadline passes unfulfilled
for President Trump to identify for punishment Kremlin-linked targets of
sanctions signed on August 2. \|\| **256 \| 2017-10-02**: President
Trump addresses the nation in regards to the mass shooting in Las Vegas,
offering his condolences to the victims and their families while
praising the first responders at the scene. \| President Trump meets
with the governors of Maine, Mississippi, Kentucky and New Hampshire at
the White House to discuss cutting federal regulations. \| President
Trump holds a bilateral meeting with Thai Prime Minister Prayuth
Chan-ocha at the White House to discuss improving trade relations. \|
President Trump has dinner with Republican members of Congress at the
White House to discuss immigration reform and improving border security.
\|\| **257 \| 2017-10-03**: President Trump meets with U.S. Virgin
Islands Governor Kenneth Mapp on board the USS Kearsarge (LHD-3) to
discuss the territory’s immediate funding needs in the aftermath of
Hurricane Maria. \| President Trump and the First Lady attend a briefing
in San Juan, Puerto Rico, with senior military personnel and government
officials, including Governor Ricardo Rossello, on hurricane recovery
efforts. \| Vice President Pence meets with representative of local
businesses, community leaders and families, with Arizona Governor Doug
Ducey in Phoenix, Arizona, to discuss efforts for tax reform. \|\| **258
\| 2017-10-04**: Secretary of State Rex Tillerson states the
administration is preparing for options ahead of the October 15, 2017,
deadline on whether Iran is complying with the 2015 nuclear accord. \|
President Trump and First Lady Melania Trump visit victims of the Las
Vegas mass shooting at University Medical Center and the first
responders who dealt with the shooter. \| It is reported that UN
Ambassador Nikki Haley has been formally reprimanded for violating the
Hatch Act. \|\| **259 \| 2017-10-05**: President Trump has a briefing
and dinner with senior military leaders at the White House to discuss
the current situation with Iran and North Korea. \| Vice President Pence
holds a meeting of the National Space Council with several White House
officials and space industry executives focusing on moving away from the
current outsourcing of manned launches and building a foundation to send
Americans to Mars. \| The United States Department of Justice reversed
an Obama-era policy that explicitly defines transgender workers as
protected under employment discrimination laws due to what qualifies as
employment discrimination under Title VII of the Civil Rights Act. \|\|
**260 \| 2017-10-06**: President Trump celebrates Hispanic Heritage
Month at the White House, and speaks of recovery efforts in Puerto Rico
and of the people suffering under the governments of Cuba and Venezuela.
\| President Trump signs a proclamation honoring October 6 as the
National day of Manufacturing, stating that jobs are coming back to the
United States with the creation of thousands of new manufacturing jobs.
\| President Trump approves an emergency declaration that will allow
federal resources to supplement local efforts and allow FEMA to
coordinate disaster relief efforts in Louisiana in preparation for
Hurricane Nate. \|\| **261 \| 2017-10-07**: Vice President Pence attends
a unity prayer walk with Las Vegas mayor Carolyn Goodman and local
officials in memory of the people killed and wounded during the Las
Vegas mass shooting. \| President Trump attends a fundraiser in
Greensboro, North Carolina, to raise funds for his reelection campaign
and the Republican National Committee. \|\| **262 \| 2017-10-08**: At
President Trump’s prior request, Vice President Pence walks out of an
NFL football game after fifteen 49er players kneel during the national
anthem. The White House says it “will not dignify any event that
disrespects our soldiers, our flag, or our national anthem”. \|\| **263
\| 2017-10-09**: Vice President Pence holds a fundraiser at Newport
Beach, California, to raise funds for Republican Congressmen and to
promote the administration’s tax-cut initiative. \|\| **264 \|
2017-10-10**: President Trump meets with former Secretary of State Henry
Kissinger at the White House, seeking his advice on dealing with North
Korea and China. \| President Trump hosts two-time winners of the
Stanley Cup, the Pittsburgh Penguins, at the White House. \| President
Trump approves a federal disaster declaration for California in response
to the Californian wildfires that will provide funding to state, local
and tribal governments to help fight the fires and rebuild. \| Vice
President Pence visits the California Office of Emergency Services at
Sacramento, California, to be briefed on operations on battling the
Californian wildfires. \|\| **265 \| 2017-10-11**: President Trump holds
a bilateral meeting with Canadian Prime Minister Justin Trudeau at the
White House to discuss NAFTA and U.S.-Canadian trade possibilities. \|
President Trump holds a campaign rally at the Harrisburg International
Airport in Harrisburg, Pennsylvania, at which he promotes his tax-cut
initiative. \|\| **266 \| 2017-10-12**: President Trump signs an
executive order which directs cabinet agencies to develop rules that
would expand access to less expensive, less comprehensive insurance
policies with fewer benefits and fewer protections for consumers than
those mandated under the Patient Protection and Affordable Care Act. \|
President Trump nominates Kirstjen Nielsen as the next Secretary of
Homeland Security, who will replace John Kelly. \| The administration
announces that the U.S. will withdraw from UNESCO, citing an
“anti-Israel bias”. \|\| **267 \| 2017-10-13**: President Trump attends
the Values Voter Summit in Washington D.C. to speak on matters such as
easing of enforcement of the Johnson Amendment and weakening the
contraception mandate in the Affordable Care Act. \| President Trump
announces at the White House that he will not certify the Iranian
nuclear deal, while giving Congress time to come up with tougher
requirements to certify compliance of the deal and imposing sanctions
Islamic Revolutionary Guard Corps. \| President Trump and First Lady
Melania Trump visit the Secret Service James J. Rowley Training Center
at Beltsville, Maryland, to inspect training procedures and equipment.
\|\| **269 \| 2017-10-15**: President Trump’s 2020 re-election campaign
files its quarterly finance report with the FEC. The filing discloses a
legal bill of 1.1m paid from campaign funds in connection with the
Russia investigations. \|\| **270 \| 2017-10-16**: President Trump
attends a rally in Greenville, South Carolina, in support of Governor
Henry McMaster to raise funds for his gubernatorial campaign. \|
President Trump has a working lunch with Senate Majority Leader Mitch
McConnell and Vice President Pence to discuss legislative issues such as
the budget, tax reform and immigration. \| Responding to questions at
the White House, President Trump makes his first public comments on the
four Special Forces soldiers killed in a suspected ISIS ambush on
October 4 and further comments on former presidents calls and letters to
the families of slain American troops during their time in office. \|\|
**271 \| 2017-10-17**: President Trump holds a bilateral meeting and
joint press conference with Greek Prime Minister Alexis Tsipras at the
White House to discuss Greek efforts to reform their economy and
military ties between both countries. \| President Trump holds a Diwali
celebration at the White House. \| President Trump addresses the
Heritage Foundation’s President’s Club Meeting, speaking of ‘American
values’ and his administration’s tax reform efforts. \| Vice President
Pence attends a small business gathering in Lancaster, New York, to
discuss the administration’s tax reform efforts. \| Trump’s nominee to
lead the White House Office of National Drug Control Policy, Tom Marino,
withdraws his nomination following news reports that Marino had
previously worked on behalf of the pharmaceutical industry. \|\| **272
\| 2017-10-18**: President Trump holds a meeting at the White House with
the Senate Finance Committee to discuss tax reform. \| President Trump
holds a phone conversation with Iowa Governor Kim Reynolds to discuss
concerns about the administration’s biofuels policy. \| The latest
version of President Trump’s travel ban is blocked by U.S. District
Judge Derrick Watson shortly before it comes into effect. \|\| **273 \|
2017-10-19**: President Trump meets with Puerto Rico Governor Ricardo
Rossello at the White House to discuss the island’s recovery efforts
after Hurricane Maria. \| President Trump attends a gala dinner at the
Kuwaiti Embassy, where the Kuwait-American Foundation is trying to raise
money for the United Nations High Commissioner for Refugees and to honor
First Lady Melania Trump for her dedication to causes affecting women
and children in the U.S. and abroad. \| President Trump nominates Joseph
J. Simons, an anti-trust lawyer to head the Federal Trade Commission,
including Noah Phillips, chief counsel for Senator John Cornyn and Rohit
Chopra, a consumer advocate to fill the remaining two seats at the
Commission. \|\| **274 \| 2017-10-20**: President Trump holds a
bilateral meeting with United Nations Secretary-General Antonio Guterres
at the White House to discuss counter-terrorism, Korea and the Middle
East. \|\| **276 \| 2017-10-22**: President Trump holds a conference
call with Republican Congressman calling on them to pass the Senate
budget and work on tax reform. \| Secretary of State Rex Tillerson
attends a co-operation council in Riyadh, Saudi Arabia, attended by
Saudi Arabia and Iraq, where he calls on Iran to remove its paramilitary
forces from Iraqi territory. \| Secretary of State Rex Tillerson holds
meetings with Qatari Foreign Minister Mohammed bin Abdulrahman Al Thani
in Doha, Qatar to find ways to resolve the diplomatic crisis between
Qatar and other Gulf states. \|\| **277 \| 2017-10-23**: President Trump
holds a bilateral meeting with Singaporean Prime Minister Lee Hsien
Loong at the White House to discuss the North Korean nuclear threat,
defence and economic relationship between both countries, whilst
overseeing the signing ceremony between Singapore Airlines and Boeing
for 13.8 billion worth of new planes. \| President Trump holds a Medal
of Honor ceremony at the White House for Captain Gary Michael Rose who
was wounded in combat during Operation Tailwind in the Vietnam War. \|
Secretary of State Rex Tillerson holds meetings in Kabul, Afghanistan
with Afghan President Ashraf Ghani and his officials on discussing
strategies on ending the conflict in the country. \|\| **278 \|
2017-10-24**: President Trump holds an awards ceremony at the White
House as part of National Minority Enterprise Development Week. \|
President Trump holds a swearing-in ceremony at the Oval Office for the
next Ambassador to the Vatican Callista Gingrich. \| President Trump
meets with Republican Senators at the Capitol to call for unity within
the party and to discuss tax reform. \| Secretary of State Rex Tillerson
holds meetings in Islamabad, Pakistan, with Pakistani Prime Minister
Shahid Khaqan Abbasi, concerning the combating of extremist fighters.
\|\| **279 \| 2017-10-25**: President Trump attends a briefing in
Dallas, Texas on the recovery efforts by Hurricane Harvey and addressing
the long-term flood mitigation plans in the state. \| President Trump
holds a fundraiser to raise funds for his re-election campaign and the
Republican National Committee, while holding a discussion round-table
with his supporters at the Belo Mansion in Dallas. \| Secretary of State
Rex Tillerson holds meetings with Indian Prime Minister Narendra Modi in
New Delhi to discuss bilateral trade and defense. \| U.S. Ambassador to
the United Nations Nikki Haley in a meeting with South Sudanese
President Salva Kiir Mayardit in Juba, South Sudan, calls on the
president to find ways to end the conflict in the country. \|\| **280 \|
2017-10-26**: President Trump signs a presidential memorandum declaring
a nationwide public health emergency and ordering all federal agencies
to take measures to reduce the number of opioid deaths in the country.
No funds are allocated from the public health emergency fund. \|\| **284
\| 2017-10-30**: Shortly following the surrender of former Trump
campaign officials Paul Manafort and Rick Gates to the FBI on twelve
charges of conspiracy and money laundering between 2006 and 2015,
President Trump states on Twitter that the charges refer to events from
“years ago” and that “there is NO COLLUSION!” \| Following the
announcement of a guilty plea from George Papadopolous concerning lying
to the FBI about meetings with Russians in 2016, Press Secretary Sanders
describes Papadopoulos having held a ‘limited’, ‘volunteer’ position in
the Trump campaign. Sanders contradicts Mueller’s indictment which
details that Papadopoulos was encouraged to meet with Russian officials
by a high-ranking Trump campaign official, named as Sam Clovis by The
Washington Post. \| The enforcement of President Trump’s ban on
transgender soldiers is blocked by U.S. District Judge Colleen
Kollar-Kotelly, stating that the President’s given reasons “do not
appear to be supported by any facts”. \|\| **285 \| 2017-10-31**:
Following a fatal vehicular attack in New York City by an Islamic
extremist, President Trump offers “condolences and prayers” to the
victims and their families. \| President Trump describes former foreign
policy aide George Papadopoulos as a “young, low level volunteer” and a
“liar”. \| Trump’s lawyer Jay Sekulow tells ABC News that presidential
pardons for Manafort, Gates and Papadopoulos are “not on the table”.
\|\| **287 \| 2017-11-02**: House Republicans publish their forthcoming
tax bill, Tax Cuts and Jobs Act of 2017, with President Trump’s
provisional approval. \| President Trump repeats his demand for the
execution of Sayfullo Saipov, the suspect in the case of the 2017 New
York City vehicular attack. \| Sam Clovis withdraws his nomination to
serve as USDA’s chief scientist. \|\| **288 \| 2017-11-03**: President
Trump leaves Washington for Hawaii prior to his five-nation tour of
Asia. \|\| **290 \| 2017-11-05**: President Trump arrives in Tokyo,
Japan during his first leg of five-nation tour of Asia. \| President
Trump meets with Japanese Prime Minister Shinzo Abe at Kasumigaseki
Country Club. \| President Trump sends his condolences to the Texan
community of Sutherland Springs following the deadliest mass shooting at
an American church. \|\| **291 \| 2017-11-06**: President Trump meets
with Emperor Akihito and Empress Michiko at the Tokyo Imperial Palace.
\| President Trump holds a joint press conference with Japanese Prime
Minister Shinzo Abe at the Akasaka Palace to discuss new arms sales to
Japan and encourages the country to shoot down North Korean missiles. \|
Commerce Secretary Wilbur Ross denies hiding his large stake in a
shipping company which has business ties to the Putin family, following
the release of the Paradise Papers. \|\| **292 \| 2017-11-07**:
President Trump arrives in Seoul, South Korea during his second leg of
five-nation tour of Asia.\[citation needed\] \| President Trump visits
U.S. and South Korean troops at Camp Humphreys.\[citation needed\] \|
President Trump holds a joint press conference with South Korean
President Moon Jae-in at the Blue House. \| At a press conference in
South Korea, President Trump announces that he “hoped to God” not to
have to use military force against North Korea, and urges Kim Jong-un to
negotiate. \| President Trump tweets his support for Republican
candidate Ed Gillespie and attacks Democratic candidate Ralph Northam in
advance of the election of a new Governor of Virginia. Northam wins.
\|\| **293 \| 2017-11-08**: President Trump addressed the National
Assembly of South Korea.\[citation needed\] \| President Trump laid a
wreath at the Seoul National Cemetery to honor the victims of the Korean
War.\[citation needed\] \| President Trump arrives in Beijing, China
during his third leg of five-nation tour of Asia.\[citation needed\] \|
President Trump meets with Chinese President Xi Jinping at the Forbidden
City.\[citation needed\] \| Former Senior Adviser to the President, Carl
Icahn, is subpoenaed for information related to his work on biofuels
policy while a part of the administration. \|\| **294 \| 2017-11-09**:
President Trump signs a number of binding and non-binding gas, aviation,
communications and food-crop deals with Chinese President Xi Jinping.
Speaking alongside President Xi Jinping in Beijing, President Trump
refers to the U.S.-Chinese trade imbalance, praising China for “taking
advantage” of prior U.S. administrations. \| President Trump holds a
joint press conference with Chinese President Xi Jinping at the Great
Hall of the People.\[citation needed\] \| The State Department rejects
an essay released by Ambassador Barbara Stephenson, which claims that
the continuing depletion of State officials under the Trump
administration will “forfeit the game to our adversaries”. \|\| **295 \|
2017-11-10**: President Trump arrives Saturday morning UTC+7 in Da Nang,
Vietnam during his fourth leg of five-nation tour of Asia.\[citation
needed\] \| In a speech to delegates, President Trump talks of “chronic
trade abuses”, and of Kim Jong-un’s “twisted fantasies of \[…\] nuclear
blackmail”, urging Russia and China to place pressure on North Korea. \|
President Trump attends the 2017 APEC summit hosted by Vietnamese
President Tran Dai Quang.\[citation needed\] \| Vice President Pence
joins other senior Republicans in stating that Republican Senate nominee
Roy Moore ought to abandon his election campaign if there is truth in
allegations of historical sexual activity with minors, as published by
The Washington Post on Thursday 9th. \|\| **296 \| 2017-11-11**:
President Trump arrives in Hanoi, Vietnam.\[citation needed\] \|
President Trump attends a state dinner hosted by Vietnamese President
Tran Dai Quang.\[citation needed\] \|\| **297 \| 2017-11-12**: President
Trump holds a joint press conference with Vietnamese President Tran Dai
Quang at the Presidential Palace.\[citation needed\] \| President Trump
holds a bilateral meeting with Vietnamese General Secretary Nguyen Phu
Trong and Prime Minister Nguyen Xuan Phuc.\[citation needed\] \|
President Trump arrives in Manila, Philippines on his fifth and final
leg of five-nation tour of Asia. \|\| **298 \| 2017-11-13**: President
Trump attends the 2017 ASEAN summit hosted by Filipino President Rodrigo
Duterte.\[citation needed\] \| President Trump holds a bilateral meeting
with Filipino President Rodrigo Duterte.\[citation needed\] \| President
Trump holds a bilateral meeting with Indian Prime Minister Narendra
Modi.\[citation needed\] \| President Trump holds a trilateral meeting
with Australian Prime Minister Malcolm Turnbull and Japanese Prime
Minister Shinzo Abe.\[citation needed\] \|\| **299 \| 2017-11-14**:
President Trump returns to Washington from Manila at the end of his
five-nation tour of Asia. \| Attorney General Jeff Sessions testifies to
the House Judiciary Committee. He states that he now recalls learning of
contact between Russians and the Trump campaign, but denies previously
lying under oath. He announces he has no reason to disbelieve those who
accuse Senate candidate Roy Moore of sexual activity with young girls.
\|\| **301 \| 2017-11-16**: President Trump visits the U.S. Capitol in
advance of the passing by House Republicans without Democratic votes
(227-205) of a 1.4tn “Tax Cut and Jobs Act” in support of Trump’s
tax-cut initiative. Among numerous proposals are included a cut in
corporate tax from 35% to 20%, and the abolition of the Family
Flexibility Credit, the estate tax and the alternative minimum tax. \|
Senators Chuck Grassley and Dianne Feinstein disclose that presidential
advisor Jared Kushner has failed to submit to them numerous documents
concerning Wikileaks and “a Russian backdoor overture”. \|\| **305 \|
2017-11-20**: President Trump announces that North Korea will be
reinstated to the United States’ list of State Sponsors of Terrorism,
from which it was removed in October 2008. \| The administration
announces an end to the temporary residency program for victims of the
2010 Haiti earthquake, effective July 2019. \| Judge William Orrick of
the Northern District Court of California replaces his preliminary
injunction with a nationwide permanent injunction declaring that section
9(a) of Executive Order 13768 was “unconstitutional on its face” and
violates “the separation of powers doctrine and deprives \[the
plaintiffs\] of their Tenth and Fifth Amendment rights.” \|\| **306 \|
2017-11-21**: President Trump and First Lady Melania Trump participate
in the National Thanksgiving Turkey Presentation.\[citation needed\] \|
President Trump and President Putin speak by telephone; Putin seeks
support for his plan to end the Syrian civil war. \| President Trump
defends Senate candidate Roy Moore from accusations of sex abuse. \|
Ivanka Trump travels to India, to represent the U.S. at the Global
Entrepreneurship Summit. \|\| **312 \| 2017-11-27**: President Trump
hosts a White House event honoring Second World War Navajo code talker
veterans. The White House later states that it is ‘ridiculous’ to
suggest that Trump’s reiteration at the event of the name ‘Pocahontas’
to describe Senator Elizabeth Warren is racist, following protestation
by the National Congress of American Indians and others. \| Leandra
English and Mick Mulvaney issue competing statements claiming leadership
of the Consumer Financial Protection Bureau. \| Politico reports that
White House ethics lawyer James Schultz has recently resigned. \|\|
**313 \| 2017-11-28**: President Trump informs reporters at the White
House of his administration’s resolve following a new North Korean
missile test which, it is believed, for the first time places Washington
D.C. within range of the KPA. \|\| **314 \| 2017-11-29**: President
Trump announces “additional major sanctions” against North Korea
following a telephone conversation with Chinese President Xi Jinping. \|
President Trump retweets anti-Muslim propaganda posted by the convicted
criminal Jayda Fransen, deputy leader of British far-right organization
Britain First. British Prime Minister May condemns the action. Trump’s
plan to visit the UK in the New Year is reportedly abandoned on the
following day. \| Trump travels to St. Charles, Missouri, to deliver a
speech promoting his tax plan. \| Kellyanne Conway is appointed to
oversee the White House’s efforts to combat the opioid epidemic. \| The
New York Times reports that Jared Kushner has been interviewed in
November by Robert Mueller’s prosecutors. \|\| **315 \| 2017-11-30**:
President Trump announces the donation of his third-quarter salary to
HHS efforts to solve the opioid epidemic. \| Press Secretary Sanders
denies reports that Secretary Tillerson is to be removed. \| Jeff
Sessions testifies at a private meeting of the House Intelligence
Committee. According to ranking member Schiff, Sessions refuses to say
whether or not President Trump asked him to hinder the Russia
investigation. \|\| **316 \| 2017-12-01**: Former NSA Michael Flynn
pleads guilty to lying to the FBI on January 24, 2017, concerning
contacts with Russian Ambassador Sergey Kislyak. \|\| **317 \|
2017-12-02**: The Senate passes a 1.5 trillion tax cut bill (51 to 49)
in support of President Trump’s tax initiative. \| President Trump
states that there was “absolutely no collusion” between his election
campaign and Russia. \|\| **318 \| 2017-12-03**: President Trump’s
lawyer John M. Dowd states that Trump knew in January 2017 that Michael
Flynn had likely lied to the FBI. \| Ambassador Nikki Haley informs UN
Secretary-General Antonio Guterres that the U.S. is to remove itself
from the UN’s 2016 New York declaration for refugees and migrants. \|\|
**319 \| 2017-12-04**: Seven of the nine judges on the Supreme Court
lift the lower court injunctions on President Trump’s third-version
travel ban, thereby permitting its enforcement against the nations of
Chad, Iran, Libya, Somalia, Syria, Yemen, Venezuela and North Korea.
Unlike previous iterations, the ban has no expiry date. \| President
Trump announces 85% and 50% reductions respectively to Utah’s Bears Ears
National Monument and Grand Staircase-Escalante National Monument. \|
President Trump formally endorses Senate candidate Roy Moore. \|\| **320
\| 2017-12-05**: Special Counsel Robert Mueller reportedly subpoenas
Deutsche Bank for records of Trump’s associates. Trump’s lawyer denies
reports that Trump’s personal financial records were subpoenaed. \|
Press Secretary Sanders denies that President Trump is planning to
create his own private global spy network, following reporting by The
Intercept and BuzzFeed News. \|\| **321 \| 2017-12-06**: President Trump
announces that the United States is to recognize Jerusalem as the
capital of Israel-the first nation to do so-and announces that the U.S.
will relocate its embassy there from Tel Aviv. \|\| **322 \|
2017-12-07**: White House Communications Director Hope Hicks is
interviewed by Special Counsel Mueller’s team as part of the Russia
investigation. \|\| **323 \| 2017-12-08**: President Trump holds a rally
at Pensacola, Florida, near the Alabama border, at which he exhorts the
Alabamian electorate to vote for Senate candidate Roy Moore on 12
December. \| Speaking at an emergency meeting of the United Nations
Security Council convened following Trump’s Jerusalem announcement of
December 6, Ambassador Haley announces that the U.S. considers an
Israeli-Palestinian peace to be “closer \[…\] than ever before”. France,
Germany, Italy, Sweden and the U.K. issue a joint statement opposing
Trump’s decision. \| Deputy National Security Adviser Dina Powell
announces her resignation. \| Hope Hicks is interviewed by Mueller’s
team for a second day. \|\| **324 \| 2017-12-09**: President Trump
attends the openings of the Mississippi Civil Rights Museum and the
Museum of Mississippi History in Jackson. \|\| **325 \| 2017-12-10**:
Vice President Pence’s office describes as “unfortunate” a decision by
Palestinian President Mahmoud Abbas to cancel a December 19 meeting
between the two during Pence’s upcoming visit to the Middle East. \|\|
**326 \| 2017-12-11**: President Trump calls for an end to “chain
migration” following an attempted bombing in New York City which injures
five people. \| President Trump signs a policy directive at the White
House, ordering NASA to reprioritize manned voyages, including a return
to the Moon and a mission to Mars. \| U.S. District Judge Colleen
Kollar-Kotelly rejects a request by the Trump administration to enforce
the President’s ban on transgender soldiers while the government’s
appeal is ongoing. \|\| **327 \| 2017-12-12**: President Trump signs the
National Defense Authorization Act’s 2018 budget, costed at 700 billion.
It provides 25m for road-based cruise missile technology, in violation
of the 1987 and 1988 Intermediate-Range Nuclear Forces Treaty. NATO
released a statement on 15 December, stating that “full compliance with
the INF Treaty is essential”. \| President Trump tweets his support for
Republican candidate Roy Moore and condemns Democratic candidate Doug
Jones on the day of Alabama’s special Senate election to fill the seat
vacated by Jeff Sessions in February 2017. Jones wins. \|\| **328 \|
2017-12-13**: Congressional Republicans reach a deal on aspects of
President Trump’s tax plan. Trump indicates that he will support a
corporate tax rate of 21%. \| It is announced that the director of
communications for the White House’s Office of Public Liaison, Omarosa
Manigault, is to resign on January 20, 2018. Contrary reports indicate
that Manigault was dismissed by Chief of Staff John Kelly and physically
removed from the White House grounds. \| Senator Chuck Grassley
announces that two of President Trump’s judicial nominees, Jeff Mateer
and Brett Talley, will not be confirmed. \|\| **329 \| 2017-12-14**:
President Trump speaks by telephone with Russian President Vladimir
Putin in an effort to engender co-operation over the North Korean
missile threat. \| The FCC repeals its net neutrality regulations. \| A
seventh U.S. Senator, Kamala Harris (in addition to Kirsten Gillibrand,
Bernie Sanders, Cory Booker, Ron Wyden, Mazie Hirono, Jeff Merkley)
calls on Trump to resign, due to the credible allegations of sexual
assault against him by 19 women. \|\| **330 \| 2017-12-15**: Speaking at
the White House, President Trump describes the FBI as acting
disgracefully and states that people are angry. Trump shortly thereafter
addresses a group of largely non-FBI graduates from a program at the FBI
National Academy in Quantico, Virginia, stating “I have your back 100%”.
\| Speaking to reporters, President Trump reiterates his description of
the matter of Russian collusion as a ‘hoax’ and replies that “we’ll see
what happens” in response to questions about the possible pardoning of
Michael Flynn. \|\| **332 \| 2017-12-17**: Russian President Vladimir
Putin telephones President Trump to thank the CIA for its assistance in
preventing a planned terrorist bombing at St. Petersburg’s Kazan
Cathedral. \|\| **333 \| 2017-12-18**: President Trump publishes his
first National Security Strategy and delivers a concomitant address,
condemning North Korea as a rogue state and positioning China and Russia
as U.S. rivals with whom his administration will attempt to “build a
great partnership”. Climate change is omitted from the strategy. \| The
U.S. blocks a resolution by the other 14 members of the UN Security
Council calling for a retraction of President Trump’s recent statement
recognizing Jerusalem as Israel’s capital. Ambassador Haley describes
the resolution as an insult which “won’t be forgotten”. \| Vice
President Pence, previously due to leave for Egypt today, delays until
January his visit to the Middle East, in order to oversee voting on
President Trump’s tax bill. \|\| **334 \| 2017-12-19**: The House of
Representatives passes a revised version of President Trump’s Tax Cuts
and Jobs Act without Democratic votes, 227-203. \| Elections for the
Virginia House of Representatives split evenly between Republicans and
Democrats following recounts. Lots are later drawn on January 4, 2018,
giving Republicans a 51-49 control of the House. \| Ambassador Haley
states that she will be “taking names” of countries who vote in favor of
the December 21 UN resolution against U.S. recognition of Jerusalem as
Israel’s capital and passing them to President Trump, who has suggested
cutting aid to countries who do so. \|\| **335 \| 2017-12-20**: The
Senate passes President Trump’s Tax Cuts and Jobs Act shortly after
midnight without Democratic votes, 51 to 48. A procedural mistake in the
House on December 19 necessitates a second vote in the House, which
later passes in favor, 224 to 201. The wide-ranging bill includes a cut
to corporate tax from 35% to 21%, a reduction to the pool of estate-tax
payers, alters each tax bracket, and reduces the rate for the highest
earners. The bill also permits oil drilling in Alaska’s Arctic National
Wildlife Refuge and removes the individual mandate from Obamacare.
President Trump announces that the bill represents a repeal of
Obamacare, and that it will be replaced by “something that will be much
better”. The legislation is financed by debt. \| The State Department
announces the approval of a 41.5m sale of small arms to Ukraine. \|\|
**336 \| 2017-12-21**: Vice President Pence arrives in Afghanistan to
visit troops and speak with Afghan leaders. In a speech at Bagram
Airfield, he announces “I believe victory is closer than ever before.”
\| The United Nations votes 128 to 9 in favor of a demand that the U.S.
retract its recent declaration concerning Jerusalem. U.S. Ambassador
Haley describes the vote as ‘null and void’. \| Press Secretary Sanders
announces that the White House does not intend to remove Robert Mueller
from the Russia investigation, and states “We look forward to seeing
this hoax wrap up very soon.” \| Judge George B. Daniels dismisses a
lawsuit by CREW against President Trump in respect of the Constitution’s
emoluments clause. Daniels rules that only Congress has authority in
such a matter, not the courts. \|\| **337 \| 2017-12-22**: President
Trump signs into law the 1.5 trillion tax bill passed by Congress on
December 20. \| President Trump retires to Mar-a-Lago for the Christmas
holiday. \| The 9th Circuit Court of Appeals rules unanimously that the
current version of the travel ban exceeds presidential authority. The
ban remains in effect during an additional appeals process. \|\| **342
\| 2017-12-27**: All ten members of the Presidential Advisory Council on
HIV/AIDS are dismissed. \| Ambassador to Panama John Feeley submits a
letter of resignation. \|\| **343 \| 2017-12-28**: President Trump
expresses disappointment following reporting by South Korean newspaper
Chosun Ilbo that China has been illegally supplying oil to North Korea.
\| In an interview with The New York Times, President Trump states that
he believes that Mueller will treat him fairly and will exonerate him.
\|\| **344 \| 2017-12-29**: Trump’s Labor Department continues the
policy of the Obama Administration of issuing waivers to banks convicted
of manipulating the global interest rate Libor. Deutsche Bank and UBS
are allowed to manage retirement funds for three years, while Barclays,
Citigroup, and JPMorgan are allowed to do the same for five years. At
the time, Trump and his businesses owe Deutsche Bank at least 130
million. \|\| **347 \| 2018-01-01**: The Trump administration announces
it will withhold the scheduled millions of military aid to Pakistan with
President Trump declaring it a terrorist “safe haven”. \| Nick Ayers
announces that Vice President Mike Pence’s chief lawyer, Mark Paoletta,
and domestic policy director, Daris Meeks, are to resign. \|\| **348 \|
2018-01-02**: President Trump tweets that his “nuclear button” is larger
and more powerful than that of Kim Jong-un. \| On Twitter, President
Trump refers to the Department of Justice as the ‘deep state’ and then
calls on it to investigate former FBI director James Comey and Hillary
Clinton’s top aide, Huma Abedin. \| Via Twitter, President Trump
threatens to cut off U.S. aid to the Palestinian Authority, claiming the
Palestinians were no longer willing to negotiate on a peace process with
the Israelis-seemingly after his December 2017 decision to recognize
Jerusalem as the capital of Israel. \|\| **349 \| 2018-01-03**:
President Trump disbands his Presidential Advisory Commission on
Election Integrity. \| President Trump issues a statement describing
Steve Bannon, former CEO of the Trump campaign, as having “very little
to do with our historic victory” and as having “lost his mind”,
following the publication of excerpts from a forthcoming book by Michael
Wolff in which Bannon is said to describe Donald Trump Jr, Paul Manafort
and Jared Kushner’s meeting with Natalia Veselnitskaya as “treasonous”
and “unpatriotic”. Wolff’s book also describes Bannon’s confidence that
Trump Sr. knew of the meeting at the time. \|\| **350 \| 2018-01-04**:
President Trump’s lawyer Charles J. Harder sends to Michael Wolff and
his publisher, Henry Holt and Company, a cease and desist letter
demanding the non-publication of Wolff’s White House expose, Fire and
Fury, due for release on January 9. Wolff’s publishers move the date of
publication forward to January 5. \| Secretary of the Interior Ryan
Zinke announces a plan to open up 90% of the U.S. coastline to oil
drilling. \|\| **351 \| 2018-01-05**: The Trump administration submits
to Congress initial details of a request for 18 billion to fund 316
miles of new barriers and upgrades to 407 miles of existing barriers
along the Mexican border. \| Wolff’s Fire and Fury is published.
President Trump describes it on Twitter as a “phony book”, “full of
lies, misrepresentations and sources that don’t exist”. \| BSEE Director
Scott Angelle announces plans to overhaul the oil-industry regulations
introduced following 2010’s Deepwater Horizon disaster \| President
Trump leaves for Camp David for a weekend of meetings with his Cabinet,
Republican party leaders, and Vice President Pence. It is reported that
a decision is expected concerning whether the administration will move
next to welfare reform or infrastructure. \| NSA Director Michael S.
Rogers announces his retirement for spring 2018. \| Following a personal
interview with President Trump, former Deutsche Bank lawyer Geoffrey
Berman takes up his position as interim U.S. attorney for the Southern
District of New York. Berman shortly afterwards appoints as his deputy
Deutsche Bank’s former U.S. general counsel Robert Khuzami. \|\| **352
\| 2018-01-06**: President Trump tweets that he is a “very stable
genius”, praising his own “mental stability”. Also within the tweet, he
says he became president “on the first try”, despite having run as a
Reform Party candidate in 2000. \| President Trump declares “everyone
found that, after a year of study, there’s been absolutely no collusion
… between us and the Russians.” Meanwhile, the special counsel
investigation into such matters are still in progress with no declared
findings. \|\| **354 \| 2018-01-08**: President Trump makes an on-field
appearance during the National Anthem at the 2018 College Football
Playoff National Championship. \| The Trump administration announces the
end in September 2019 to the Temporary Protected Status granted to
nearly 200,000 Salvadorans by then-president George W. Bush following
the 2001 El Salvador earthquakes. \| President Trump submits to the
Senate 21 re-nominations for judicial posts, including two rated ‘not
qualified’ by the ABA. \| Vice President Pence describes Fire and Fury
as a “book of fiction”, while saying he has not read the book and does
not intend to. \|\| **355 \| 2018-01-09**: President Trump holds a
bipartisan meeting with members of Congress discussing the topic of
immigration. \| District judge William Alsup rules that the DACA program
must remain in place while litigation continues over the Trump
administration’s September 5 decision to end it. The next morning, Trump
describes the U.S. court system as “broken and unfair”. \| Secretary
Zinke announces that Florida will be exempted from oil drilling under
the new policy announced on January 4. \|\| **356 \| 2018-01-10**:
President Trump describes Senator Dianne Feinstein as “sneaky” and a
“disgrace” following her unilateral publication on January 9 of the
Simpson testimony of August 2017 concerning research into potential
crimes in respect of the 2016 election. \| President Trump reiterates
that he will be reviewing libel law, describing the current law as “a
sham and a disgrace”. \| President Trump holds a bilateral meeting and
joint press conference with Nordic Prime Minister Erna Solberg at the
White House. \|\| **357 \| 2018-01-11**: The Trump administration
announces new state guidelines that Medicaid recipients may be required
to work or volunteer, or enroll in education. \| The Washington Post
reports that President Trump, in a meeting with Senators Lindsey Graham
(R-SC) and Dick Durbin (D-IL) regarding immigration law reform, referred
to Haiti and African countries as “shithole countries” and expressed
preference for immigrants from Norway. On the following day, Trump
denies using the term, but says he used tough language in regards to the
countries; Senator Durbin affirmed that Trump had made those remarks. \|
Vice President Pence visits Las Vegas, Nevada, and speaks at nearby
Nellis Air Force Base. \|\| **358 \| 2018-01-12**: President Trump
proclaims Martin Luther King Jr. Day for January 15. \| President Trump
cancels a planned visit to the UK, blaming his predecessor, Barack
Obama, for a “bad deal” on the new embassy due to be opened in London,
despite the fact it was agreed under George W. Bush. \| The Wall Street
Journal reports that, in October 2016, President Trump’s lawyer, Michael
Cohen, arranged a payment of 130,000 to the adult-film actress Stormy
Daniels in exchange for her silence regarding a 2006 extramarital
affair. Cohen denies that Trump had sexual relations with Daniels.
Fellow adult-film actress Alana Evans said Daniels told her she had
“ended up with Donald in his hotel room”. \| Citing disagreements with
the Trump administration, John Feeley announces his resignation as U.S.
Ambassador to Panama, effective March 9, 2018. \|\| **359 \|
2018-01-13**: President Trump is briefed at the White House concerning
Hawaii’s emergency management protocol following a public disturbance
due to a false alarm of an incoming ballistic missile. \|\| **361 \|
2018-01-15**: Secretary of State Rex Tillerson co-hosts with Canadian
Foreign Affairs Minister Chrystia Freeland the first of two days of
talks in Vancouver concerning the North Korea crisis. \| Nine of the
twelve members of the National Park System Advisory Board resign
following Interior Secretary Zinke’s refusal to convene meetings. \| The
Wall Street Journal reports that Jared Kushner was warned in early 2017
by U.S. intelligence officials that his friend Wendi Deng Murdoch may be
a Chinese spy. \|\| **362 \| 2018-01-16**: President Trump holds a
bilateral meeting and joint press conference with Kazakhstani President
Nursultan Nazarbayev at the White House. \| President Trump’s former
Chief Strategist Steve Bannon is questioned at a private sitting of the
House Intelligence Committee. He is issued with a subpoena during the
meeting upon citing executive privilege to refuse questions about the
Trump transition and administration, but maintains his refusal. \|\|
**363 \| 2018-01-17**: In an Oval Office interview for Reuters,
President Trump accuses Russia of harming Chinese/American efforts to
solve the ongoing North Korean nuclear crisis. \| In Touch Weekly
publishes excerpts from a 2011 interview with adult-film actress Stormy
Daniels alleging a 2006 extramarital affair with Trump. The magazine
describes her passing a polygraph and her friend’s and ex-husband’s both
corroborating the interview. \| President Trump announces the winners of
the “Fake News Awards”, despite criticism from Republican senators Jeff
Flake and John McCain. \|\| **364 \| 2018-01-18**: President Trump
delivers a speech at a factory near Pittsburgh, Pennsylvania. He offers
his support for Republican candidate Rick Saccone in the upcoming March
13 special election for Pennsylvania’s 18th district. \| The House
passes a short-term government budget in advance of a deadline of
midnight January 19-20. \| It is widely reported that Hungarian police
have an active arrest warrant, issued on September 17, 2016, against
former Trump White House advisor Sebastian Gorka. The warrant concerns
alleged abuse of firearms. \|\| **365 \| 2018-01-19**: President Trump
states on Twitter that Democratic votes will be needed in the Senate to
prevent a government shutdown at midnight. He writes, “but they want
illegal immigration and weak borders”. \| German periodical Manager
Magazin reports that Deutsche Bank has presented to Germany’s financial
authority, BaFin, evidence concerning “suspicious money transfers” by
White House advisor Jared Kushner. MM reports that this information is
due to be handed to Robert Mueller’s inquiry. Deutsche Bank on January
22 denies the report, and announces that it is taking legal action. \|\|
**366 \| 2018-01-20**: A federal government shutdown begins, after the
Senate fails to pass a continuing resolution to maintain funding for the
government. \| Vice President Pence arrives in Cairo, Egypt at the start
of a tour of Africa and the Middle East. \| The second year of the Trump
presidency begins. \|\| **367 \| 2018-01-21**: Vice President Pence
meets with King Abdullah II of Jordan in Amman. Abdullah criticizes the
decision to recognize Jerusalem as the Israeli capital. Pence reaffirms
U.S. respect towards Jordan’s role as the guardian of Jerusalem’s
Islamic holy sites. \|\| **368 \| 2018-01-22**: During the third day of
the federal government shutdown, President Trump accuses the Democratic
Party of precipitating the shutdown “in the interests of their far left
base”. \| President Trump signs a bi-partisan bill, which passed
Congress with support from both parties, officially ending the
government shutdown that began three days earlier. The bill provides
funds until February 8, 2018. \| Vice President Pence delivers a speech
at Israel’s Knesset, announcing that the U.S. will relocate its embassy
from Tel Aviv to Jerusalem by the end of 2019. A number of Arab members
of Parliament are ejected while protesting. \|\| **369 \| 2018-01-23**:
Vice President Pence visits Jerusalem’s Western Wall. \|\| **370 \|
2018-01-24**: President Trump announces during remarks at the White
House that he is willing to testify to Mueller under oath, stating, “I
would love to do it, and I would like to do it as soon as possible.” \|
The Senate confirms Alex Azar as the 24th U.S. Secretary of Health and
Human Services in a vote of 55-43. \|\| **371 \| 2018-01-25**: President
Trump arrives in Davos, Switzerland to attend the 2018 Davos World
Economic Forum. He is the first U.S. President to personally attend the
annual Davos conference since President Bill Clinton in 2000. U.S.
Treasury Secretary Steve Mnuchin is head of the U.S. delegation, which
is the largest ever to attend the forum. \| The New York Times first
reports that President Trump ordered the dismissal of the special
counsel, Robert Mueller, in June 2017, on three alleged pretexts of
conflicts of interest, but retreated upon the threatened resignation of
White House counsel Don McGahn; this elevated concerns of possible
obstruction of justice. The report is confirmed by The Washington Post.
\| First Lady Melania Trump visits the United States Holocaust Memorial
Museum in Washington D.C. \|\| **372 \| 2018-01-26**: President Trump
denies ordering the dismissal of Mueller, describing it as ‘fake news’.
\| President Trump returns to the White House from Switzerland. \|\|
**375 \| 2018-01-29**: The Trump administration submits five reports to
Congress as mandated by the Countering America’s Adversaries Through
Sanctions Act (CAATSA), including two versions (one classified) of the
report “regarding senior political figures and oligarchs in the Russian
Federation and Russian parastatal entities”. The unclassified list
published the following day by the Treasury Department contains names of
210 people, including 96 Russian tycoons close to president Vladimir
Putin with wealth of 1 billion or more, as well as top Russian
statespersons and officials, excluding Vladimir Putin, all information
having been drawn from public sources. \| Alex Azar is sworn in as the
24th U.S. Secretary of Health and Human Services. \| Deputy FBI Director
Andrew McCabe resigns from his position, but remained as part of the
FIB, after criticism from President Trump in preceding weeks. McCabe had
been expected to step down in March. \|\| **376 \| 2018-01-30**:
President Trump delivers his first official State of the Union Address
with a wide-ranging speech covering matters of natural disasters,
terrorism, immigration, economic growth, patriotism and the U.S. nuclear
arsenal. He calls on Congress for a 1.5 trillion infrastructure
investment bill and an end to political division. \| The White House
confirms that President Trump has signed an order keeping open the
Guantanamo Bay detention camp in Cuba. \| Treasury Secretary Steve
Mnuchin announces that U.S. sanctions against Russian oligarchs will
follow the previous day’s list, and denies that the administration is
“slow-walking” the process. \|\| **377 \| 2018-01-31**: Doctor Brenda
Fitzgerald resigns as Director of the Center for Disease Control over
conflicts of interest. \|\| **378 \| 2018-02-01**: Tom Shannon, the
United States Under Secretary of State for Political Affairs, announces
he will be resigning for personal reasons. The State Department’s
third-ranking official and its most senior career diplomat says he will
stay on until a successor is named. \|\| **379 \| 2018-02-02**:
President Trump declassifies the Nunes memo and authorizes Congress to
release it. \|\| **382 \| 2018-02-05**: At a speech in Cincinnati, Ohio,
President Trump claims that Congressional Democrats, who “were like
death and un-American” in not applauding during his State of the Union
speech, were “treasonous” and that “we call that treason”. \|\| **383 \|
2018-02-06**: While Congress was preparing a continuing resolution for a
temporary budget, President Trump declared, “I’d love to see a shutdown”
if American immigration laws were not tightened. He also said “it’s
worth it for our country”. \|\| **384 \| 2018-02-07**: White House Staff
Secretary Rob Porter resigns from his position following two public
allegations of spousal abuse. \| Associate Attorney General Rachel Brand
resigns in order to enter the private sector. \|\| **385 \|
2018-02-08**: President Trump speaks at the National Prayer Breakfast.
\|\| **386 \| 2018-02-09**: Federal funding lapsed for the second time
in 2018 after Republican Senator Rand Paul delayed the vote on a
temporary appropriations bill by objecting to measures requiring
unanimous consent to expedite the parliamentary process. \| Congress
passes a budget bill to end the federal funding gap within six hours;
President Trump signs the bill into law. \|\| **389 \| 2018-02-12**:
President Trump sends his 4.4 trillion 2019 budget proposal to Congress.
\| President Trump introduces his 1.5 trillion federal infrastructure
plan to several governors and mayors at the White House. \|\| **390 \|
2018-02-13**: President Trump’s personal lawyer Michael Cohen
acknowledged that in 2016 he paid 130,000 of his own money to adult-film
actress Stormy Daniels. Cohen further said that The Trump Organization
and the Trump campaign were not involved in the payment and did not
reimburse him. It was earlier reported that the payment was hush money
for Daniels’ silence regarding an alleged extramarital affair with Trump
in 2006. \|\| **392 \| 2018-02-15**: President Trump addresses the
nation in regards to the school shooting in Parkland offering his
condolences to the victims and their families. \|\| **393 \|
2018-02-16**: The New Yorker reports that President Trump had a
nine-month extramarital affair with Playboy model Karen McDougal from
June 2006, citing handwritten memoirs by McDougal provided by her
friend. The New Yorker also corroborated a 2016 Wall Street Journal
report that American Media, Inc (AMI) had paid 150,000 for exclusive
rights to McDougal’s story, but never published it. AMI has described
the story as not credible, and a spokesperson for the White House denied
the affair. \| President Trump and First Lady Melania Trump visit
victims of the Parkland school shooting at Broward Health North Medical
Center. \|\| **397 \| 2018-02-20**: President Trump orders the
Department of Justice to prepare regulations to ban devices that allow
semi-automatic rifles to become fully automatic, such as the bump stocks
used in the 2017 Las Vegas shooting. \|\| **400 \| 2018-02-23**:
President Trump gives a speech in Oxon Hill, Maryland to the 2018
Conservative Political Action Conference. \| President Trump holds a
bilateral meeting and joint press conference with Australian Prime
Minister Malcolm Turnbull at the White House. \|\| **401 \|
2018-02-24**: A Democratic memo titled Correcting the Record-The Russia
Investigation in response to the Nunes memo, is released after redacting
by the FBI. \|\| **402 \| 2018-02-25**: President Trump attends the
National Governors Association dinner.\[citation needed\] \|\| **404 \|
2018-02-27**: Josh Raffel, a senior communications aide, announced his
resignation from the administration. \| Joseph Yun, the top diplomat in
charge of America’s Korean policy, announces his resignation. \|\| **405
\| 2018-02-28**: At the lying in honor of evangelical preacher Billy
Graham in the U.S. Capitol rotunda, President Trump and congressional
leaders praise Graham. \| A day after being interviewed by the U.S.
House Intelligence Committee, White House Communications Director Hope
Hicks submits her resignation. \|\| **406 \| 2018-03-01**: Two-time NBA
champions Golden State Warriors toured the National Museum of African
American History and Culture as an alternative to the traditional White
House visit. \| The U.S. Fish and Wildlife Service removes the blanket
ban on imports of sport-hunted trophies of elephants from certain
African countries originally imposed by the Obama administration. The
trophies will now be evaluated on a case-by-case basis. The organization
also withdrew several Endangered Species Act findings regarding African
elephants, lions and the bontebok antelopes. \| Roberta Jacobson, the
Ambassador to Mexico, resigns from her post. \|\| **408 \| 2018-03-03**:
In a private speech to Republican donors at Mar-a-Lago, President Trump
says “it’s great” that Chinese President Xi Jinping was able to become
“president for life”, and that “maybe we’ll have to give that a shot
some day.” \|\| **410 \| 2018-03-05**: President Trump holds a bilateral
meeting with Israeli Prime Minister Benjamin Netanyahu at the White
House. \|\| **411 \| 2018-03-06**: The U.S. Office of Special Counsel
(OSC) says Counselor to the President Kellyanne Conway violated federal
law in the form of the Hatch Act during two television interviews in
2017 by advocating for the defeat of Doug Jones and the election of Roy
Moore for Alabama’s election for a Senate seat. The White House has
disputed this finding by the OSC. \| Chief economic adviser Gary Cohn
announces plan to resign after President Trump announced he would impose
tariffs on steel and aluminum imports. \| President Trump holds a
bilateral meeting and joint press conference with Swedish Prime Minister
Stefan Lofven at the White House. \|\| **412 \| 2018-03-07**: White
House Press Secretary Sarah Huckabee Sanders says President Trump’s
personal attorneys have won an arbitration case against adult-film
actress Stormy Daniels.NBC News reports that Trump’s lawyer, Michael
Cohen, on February 27 initiated a private arbitration case against
Daniels and obtained a restraining order that states that Daniels will
face penalties if she discusses, in public, her alleged relationship
with Trump. Daniels has filed a lawsuit that her non-disclosure
agreement regarding her alleged relationship with Trump is invalid
because Trump never signed it. \| U.S. Forest Service Chief Tom Tooke
resigns from his post. \|\| **413 \| 2018-03-08**: President Trump signs
proclamations which will impose tariffs on imported steel and aluminum
from most countries in 15 days. Canada and Mexico are initially exempted
from these tariffs while they talk with the U.S. about renegotiating
NAFTA. \| President Trump accepts an invitation to meet with North
Korean Leader Kim Jong-un by May 2018. \| President Trump meets with
video-game executives to discuss how violent video games might
contribute to mass shootings. \|\| **414 \| 2018-03-09**: President
Trump pardons Kristian Saucier, who was convicted of unauthorized
possession and retention of national defense information. \| White House
Press Secretary Sarah Huckabee Sanders says the White House would need
to see “concrete and verifiable steps” toward the denuclearization of
North Korea before Trump would meet with Kim Jong-un. An unidentified
Trump official tells The Wall Street Journal that Trump has still
accepted Jong-un’s invitation. \|\| **415 \| 2018-03-10**: President
Trump holds a rally at the Pittsburgh International Airport to support
Rick Saccone in an upcoming special election. He introduces his 2020
campaign slogan: “Keep America Great!” \|\| **416 \| 2018-03-11**: The
Trump administration proposes gun and school safety measures, including
improving the system of background checks and training school personnel
to handle firearms. \|\| **417 \| 2018-03-12**: Citing national security
concerns, President Trump blocks Broadcom’s proposed acquisition of
Qualcomm. \|\| **418 \| 2018-03-13**: President Trump fires Rex
Tillerson as Secretary of State, names former CIA director Mike Pompeo
as the new Secretary of State, and nominates Gina Haspel as the next
director of the CIA. Deputy Secretary of State John J. Sullivan becomes
Acting Secretary of State. \| Steve Goldstein, the United States Under
Secretary of State for Public Diplomacy and Public Affairs and fourth
ranking diplomatic official, is fired by the White House. Trump
designates Heather Nauert as Goldstein’s replacement. \| John McEntee, a
long-time personal assistant to President Trump, is fired and escorted
from the White House. McEntee then joins Trump’s re-election campaign as
a senior adviser, along with Katrina Pierson. \|\| **419 \|
2018-03-14**: President Trump chooses Larry Kudlow as director of the
National Economic Council, replacing Gary Cohn. \|\| **420 \|
2018-03-15**: The Trump administration uses the Countering America’s
Adversaries Through Sanctions Act to impose financial sanctions on the
13 Russian government hackers and spy agencies indicted in the Special
Counsel investigation. \| President Trump holds a bilateral meeting with
Irish Taoiseach Leo Varadkar at the White House. \|\| **421 \|
2018-03-16**: Andrew McCabe, former acting director of the FBI who was
due to retire with benefits in two days, was fired from the FBI by
Attorney General Jeff Sessions on the recommendation of FBI disciplinary
officials for “lack of candor”. \|\| **425 \| 2018-03-20**: The Kremlin
announces President Trump’s call to congratulate Russian President
Vladimir Putin on his election victory. National security advisers
warned Trump against the call. \| President Trump meets with Crown
Prince Mohammad bin Salman of Saudi Arabia in the Oval Office. \|\|
**427 \| 2018-03-22**: H.R. McMaster resigns as National Security
Adviser and John Bolton, a former ambassador to the United Nations, is
named to succeed him. \|\| **428 \| 2018-03-23**: The White House issues
a memorandum on Jim Mattis’s recommended military policies, which state
that transgender personnel are “disqualified from military service
except under limited circumstances”. \| The U.S. charges and sanctions
nine Iranians and the Iranian company Mabna Institute for hacking and
attempting to hack hundreds of universities on behalf of the Iranian
government. \|\| **431 \| 2018-03-26**: The White House announces the
expulsion of 60 Russian diplomats. \|\| **433 \| 2018-03-28**: President
Trump fires Secretary of Veteran Affairs David Shulkin and nominates
White House doctor Ronny L. Jackson to replace him. \|\| **436 \|
2018-03-31**: Rex Tillerson’s last day as Secretary of State. \|
President Trump nominates CIA Director Mike Pompeo as the next Secretary
of State. \|\| **438 \| 2018-04-02**: President Trump and First Lady
Melania Trump participate in the White House Easter Egg Roll. \| Kremlin
foreign policy aide Yuri Ushakov claims Trump invited Russian President
Vladimir Putin to the White House. \|\| **439 \| 2018-04-03**: President
Trump holds a joint press conference with the leaders of three Baltic
states at the White House: Estonian President Kersti Kaljulaid, Latvian
President Raimonds Vejonis and Lithuanian President Dalia Grybauskaite.
\|\| **440 \| 2018-04-04**: President Trump signs a proclamation
directing the deployment of the National Guard to the U.S.-Mexico border
to fight illegal immigration. \| President Trump attends a campaign
rally in White Sulfur Springs, West Virginia. \|\| **445 \|
2018-04-09**: After the FBI and federal prosecutors raid the home, hotel
room, and office of President Trump’s personal attorney, Michael Cohen,
Trump brands the raid as “an attack on our country in a true sense”. \|
Regarding firing special counsel Robert Mueller, President Trump says,
“Many people have said you should fire him”, and “We’ll see what
happens”. \| President Trump meets with military leaders to discuss a
response to poison gas attacks in Syria. \|\| **446 \| 2018-04-10**: The
White House confirms the resignation of Homeland Security advisor Thomas
Bossert and National Security Council spokesman Michael Anton. \|
President Trump holds a bilateral meeting with Emir Tamim bin Hamad Al
Thani of Qatar at the White House. \| President Trump hosts the NCAA
football champion Alabama Crimson Tide on the south lawn of the White
House. \|\| **447 \| 2018-04-11**: President Trump signs a bill that
reduces legal protections for websites that enable sex trafficking. \|
Nadia Schadlow, deputy national security adviser for strategy, resigns
effective April 27. \| President Trump hires a new member for his legal
team, Joanna Hendon, a partner at the New York firm Spears + Imes. \|\|
**448 \| 2018-04-12**: President Trump launches a task force to “conduct
a thorough evaluation of the operations and finances of the United
States Postal System”. \| President Trump tweets a warning that “an
attack on Syria could be very soon or not soon at all!” \|\| **449 \|
2018-04-13**: President Trump pardons Scooter Libby, the former chief of
staff for Vice President Dick Cheney in the George W. Bush
Administration. As a result of the Plame investigation into the leaking
of an undercover CIA agent’s identity, Libby had been found guilty of
making false statements, obstruction of justice and lying under oath. \|
President Trump sends a series of tweets attacking James Comey, the
fired FBI director, as a liar and a “slimeball” and suggests Comey
should be in jail. \| President Trump authorizes joint military strikes
with France and the United Kingdom against Syria and challenges Iran and
Russia to decide if they will continue to support the Assad regime.
President Trump in his address to the nation from the White House stated
“A short time ago, I ordered the U.S. Armed Forces to launch precision
strikes on targets associated with the chemical weapons capabilities of
Syrian dictator, Bashar al-Assad, a combined operation with the armed
forces of France and the United Kingdom is now under way.” \| President
Trump says the United States may rejoin the Trans-Pacific Partnership.
\|\| **452 \| 2018-04-16**: President Trump’s new lawyer, Joanna Hendon,
a partner at New York’s Spears + Imes law firm, represents him at a
hearing concerning Michael Cohen. \|\| **453 \| 2018-04-17**: President
Trump meets with Japanese Prime Minister Shinzo Abe for the first of two
days of meetings and events to discuss trade, security, and Trump’s
expected meeting with North Korean leader Kim Jong-un this spring. \|
President Trump announces that CIA director Mike Pompeo had travelled to
North Korea over the Easter Weekend and met with Kim Jong-un to discuss
and plan for Trump’s visit. \| UN Ambassador Nikki Haley responds to a
claim by White House economic adviser Larry Kudlow that she was confused
when she announced a rollout of sanctions on Russia by commenting, “With
all due respect, I don’t get confused.” \|\| **454 \| 2018-04-18**:
President Trump and Japanese Prime Minister Shinzo Abe conduct a joint
news conference after their second day of meetings. \|\| **455 \|
2018-04-19**: Rudy Giuliani, as well as Jane and Marty Raskin, join
President Trump’s legal team. The Raskins are married law partners based
in Coral Gables, Florida. \|\| **456 \| 2018-04-21**: President Trump
uses Twitter to attack New York Times reporter Maggie Haberman following
an article she wrote about his poor treatment of Michael Cohen and that
Cohen may cooperate with prosecutors as a result. \|\| **457 \|
2018-04-22**: President Trump tweets a claim that North Korea has agreed
to denuclearize. \|\| **458 \| 2018-04-23**: French President Emmanuel
Macron, accompanied by his spouse, begins a three-day state visit, the
first during the Trump presidency. \| The Senate foreign relations
committee votes 11-9 in favor of Mike Pompeo’s nomination for secretary
of state. \|\| **459 \| 2018-04-24**: The Senate Committee on Veterans’
Affairs announces a delay in the hearing for Trump veterans
administration nominee Ronny Jackson. \| President Trump holds a
bilateral meeting and joint press conference with French President
Emmanuel Macron at the White House. \| President Trump and First Lady
Melania Trump host their first state dinner in honor of French President
Emmanuel Macron and his wife, Brigitte. \|\| **460 \| 2018-04-25**:
French President Emmanuel Macron addresses a joint meeting of the
members of Congress. \| Bryan Rice, head of the Bureau of Indian
Affairs, resigns. \|\| **461 \| 2018-04-26**: Dr. Ronny Jackson
withdraws his nomination to head the Department of Veterans Affairs. \|
The Senate confirms Mike Pompeo as the 70th U.S. Secretary of State in a
vote of 57-42. \| President Trump withholds some classified documents as
NARA releases 19,045 more documents on the assassination of former
President John F. Kennedy. They are to be released in 2021. \|\| **462
\| 2018-04-27**: President Trump holds a bilateral meeting and joint
press conference with German Chancellor Angela Merkel at the White
House. \|\| **465 \| 2018-04-30**: Stormy Daniels files a defamation
lawsuit against Trump for his “total con job” tweet about the forensic
sketch of a man who allegedly threatened her in 2011. \| President Trump
holds a bilateral meeting and joint press conference with Nigerian
President Muhammadu Buhari at the White House. \| Thomas Homan, acting
director of ICE, announces his retirement effective June 2018. \|\|
**466 \| 2018-05-01**: President Trump presents the Commander-in-Chief’s
Trophy to the Army Black Knights football team for its victory over both
Air Force and Navy last year. \| During an interview with NBC News,
Harold Bornstein, Donald Trump’s longtime personal medical doctor for
over 35 years, says Keith Schiller, director of Oval Office operations
for the White House, another unnamed “large man”, and Alan Garten, The
Trump Organization chief legal officer, had taken Donald Trump’s medical
records from Bornstein’s office on February 3, 2017, without obtaining a
Health Insurance Portability and Accountability Act (HIPAA) release
statement signed by Donald Trump. \|\| **467 \| 2018-05-02**: President
Trump announces plans to replace retiring White House lawyer Ty Cobb
with former President Clinton’s impeachment lawyer, Emmet Flood. \|\|
**468 \| 2018-05-03**: President Trump speaks at the National Day of
Prayer service in the Rose Garden. \|\| **469 \| 2018-05-04**: Over the
preceding week, four EPA officials have resigned: Albert “Kell” Kelly,
the top Superfund advisor; Pasquale Perrotta, the head of Administrator
Pruitt’s security detail; Associate Administrator Liz Bowman; and today
John Konkus, deputy Associate Administrator for public affairs. \| The
Trump administration ends temporary protected status for Hondurans,
leaving potentially 57,000 people vulnerable to deportation. \|
President Trump and Vice President Pence speak at National Rifle
Association’s annual convention in Dallas, Texas. \|\| **470 \|
2018-05-05**: President Trump attends a fundraiser for the RNC in
Cleveland, Ohio. \|\| **472 \| 2018-05-07**: First Lady Melania Trump
announces the launch of her Be Best anti-cyber bullying initiative. \|\|
**473 \| 2018-05-08**: The White House denies a New York Times report
that President Trump has privately told French President Emmanuel Macron
the U.S. is withdrawing from the Iran nuclear deal. \| President Trump
announces in a speech that the U.S. will withdraw from the Obama-era
Iran nuclear deal and reinstate sanctions. \|\| **474 \| 2018-05-09**:
R. Timothy Ziemer, the official on the National Security Council
responsible for global health security and biodefense, is dismissed and
his position is abolished. \|\| **475 \| 2018-05-10**: President Trump
welcomes three American detainees released from North Korea. \| Homeland
Security director Kirstjen Nielsen considers resigning after being
berated by the president during a cabinet meeting. \|\| **476 \|
2018-05-11**: Kelly Sadler, a White House official, mocks Senator John
McCain, saying his opposition to Gina Haspel, Trump’s nominee for CIA
director, “doesn’t matter, he’s dying anyway”. \|\| **479 \|
2018-05-14**: A report shows the Trump Administration is concerned about
chemically polluted water supplies near military installations. \|\|
**480 \| 2018-05-15**: The Trump Administration eliminates the White
House’s top cyber security policy role. Rob Joyce, the coordinator, is
no longer at the White House. \| UN Ambassador Nikki Haley walks out of
UN Security Council as Palestinian Ambassador Riyad H. Mansour begins
his remarks. \|\| **481 \| 2018-05-16**: President Trump submits a
disclosure of personal finances which is required by the Office of
Government Ethics. Trump acknowledges that Michael Cohen was paid
between 100,000 and 250,000 in 2017. \| President Trump meets with
Uzbekistani President Shavkat Mirziyoyev at the White House. \|\| **482
\| 2018-05-17**: Gina Haspel is confirmed by the Senate as the first
female CIA director. \| President Trump meets with NATO Secretary
General Jens Stoltenberg at the White House. \|\| **483 \| 2018-05-18**:
President Trump announces the nomination of acting VA secretary Robert
Wilkie to head the agency. At the same White House event he expressed
his “sadness and heartbreak” over the Santa Fe school shooting. \| First
Lady Melania Trump is released from Walter Reed National Military
Medical Center after a five-day stay for kidney surgery. \| Mark Inch,
the director of Federal Prisons, resigns. \|\| **486 \| 2018-05-21**:
President Trump requests the Justice Department investigate whether his
campaign was “infiltrated” by the FBI. The inspector general will review
the FBI’s counterintelligence investigation of the 2016 Trump campaign.
\| Treasury secretary Steve Mnuchin announces the administration will
not implement its planned tariffs on China. \|\| **487 \| 2018-05-22**:
President Trump holds a bilateral meeting with South Korean President
Moon Jae-in at the White House to discuss the denuclearization of North
Korea. \| Reporters from CNN and The Associated Press are denied entry
and forcibly removed from the PFAS National Leadership Summit event at
the EPA where Scott Pruitt was to speak. \| President Trump signs the
Securely Expediting Clearances Through Reporting Transparency Act of
2018. \|\| **489 \| 2018-05-24**: President Trump posthumously pardons
heavyweight boxing champ Jack Johnson. \| President Trump cancels the
proposed June nuclear summit with North Korea via a letter to Kim
Jong-un. \|\| **490 \| 2018-05-25**: President Trump delivers the
commencement address at the U.S. Naval Academy in Annapolis, Maryland.
\|\| **493 \| 2018-05-28**: President Trump performs a wreath-laying
ceremony at the Tomb of the Unknown Soldier at the Arlington National
Cemetery and gives a speech honoring those who have died fighting for
the U.S. \|\| **497 \| 2018-06-01**: President Trump announces that the
North Korea-United States summit would resume as scheduled for June 12
in Singapore after he met North Korean general Kim Yong-chol at the
White House. \|\| **502 \| 2018-06-06**: Raj Shah announces via email
that Kelly Sadler, a member of the White House communications staff, is
“… no longer employed within the Executive Office of the President”.
\|\| **503 \| 2018-06-07**: President Trump holds a bilateral meeting
and joint press conference with Japanese Prime Minister Shinzo Abe at
the White House. \|\| **504 \| 2018-06-08**: President Trump attends the
44th G7 summit with world leaders of G7 in La Malbaie, Canada. \|
President Trump holds bilateral meetings with Canadian Prime Minister
Justin Trudeau and French President Emmanuel Macron. \|\| **505 \|
2018-06-09**: After President Trump leaves the 44th G7 summit early, he
withdraws the United States’ endorsement of a joint communique by the
G7, and labels Canadian Prime Minister Justin Trudeau “Very dishonest +
meek”. \| President Trump also addresses Trudeau by saying the Trump
tariffs targeting Canada “are in response to his of 270% on dairy!” In
the tweet, Trump did not cite national security, the legal basis for
implementing the tariff. \|\| **506 \| 2018-06-10**: Trade adviser Peter
Navarro says there is “a special place in hell for” Canadian Prime
Minister Justin Trudeau for having employed “bad faith diplomacy with
President Donald J. Trump and then tries to stab him in the back on the
way out the door … that comes right from Air Force One.” \| Politico
reports that Trump frequently and routinely would tear up papers he
received, resulting in government officials’ taping them together for
archiving to ensure he had not violated the Presidential Records Act.
\|\| **507 \| 2018-06-11**: President Trump holds a bilateral meeting
with Singaporean Prime Minister Lee Hsien Loong in the Istana Palace.
\|\| **508 \| 2018-06-12**: President Trump and North Korean Leader Kim
Jong-un participate in a summit at the Capella Hotel in Sentosa,
Singapore. \| President Trump and North Korean Leader Kim Jong-un sign a
joint declaration titled “Joint Statement of President Donald J. Trump
of the United States of America and Chairman Kim Jong Un of the
Democratic People’s Republic of Korea at the Singapore Summit”. \|\|
**511 \| 2018-06-15**: The Department of Homeland Security states that
between April 19 and May 31, 2018, there were 1,995 migrant children
separated at the Mexico-United States border from 1,940 adults who are
being held for criminal prosecution for an illegal border crossing. \|
President Trump says in response to the situation: “I hate to see
separation of parents and children … I hate the children being taken
away.” Trump then falsely blames the Democrats for the situation when it
was the Trump administration’s own “zero tolerance” policy announced on
April 6, 2018, which is responsible for spurring the separations. He
also says he “certainly wouldn’t sign the more moderate” immigration
bill proposed by House leaders with input from moderate Republicans and
the White House. \| The Washington Post quotes a White House official as
saying that Trump’s decision to enforce the current immigration law is
“force people to the table” to negotiate on laws in Congress. Meanwhile,
Trump tweets: “Any Immigration Bill MUST HAVE full funding for the Wall,
end Catch + Release, Visa Lottery and Chain, and go to Merit Based
Immigration.” \| In June 2018, Trump falsely claims that a report by
Justice Department Inspector General Michael E. Horowitz “totally
exonerates” him, despite the report’s having nothing to do with the 2017
special counsel investigation, the Trump campaign or Russia. (The report
was instead focused on the FBI’s 2016 investigation of the Hillary
Clinton email controversy.) \|\| **515 \| 2018-06-19**: President Trump
meets with King Felipe VI and Queen Letizia of Spain at the White House.
\|\| **521 \| 2018-06-25**: President Trump holds a bilateral meeting
with King Abdullah II of Jordan at the White House. \|\| **523 \|
2018-06-27**: President Trump holds a bilateral meeting with Portuguese
President Marcelo Rebelo de Sousa at the White House. \| Senior Supreme
Court Justice Anthony Kennedy announces his retirement from the Supreme
Court, effective July 31, 2018. \|\| **528 \| 2018-07-02**: President
Trump holds a bilateral meeting with Dutch Prime Minister Mark Rutte at
the White House. \|\| **530 \| 2018-07-04**: President Trump hosts
military personnel and their families for a picnic and fireworks show at
the White House as part of Independence Day celebrations. \|\| **531 \|
2018-07-05**: Scott Pruitt resigns as EPA Administrator, effective July
6, amidst fifteen federal investigations by various government ethics
agencies for his assorted management scandals (see here for
descriptions.) \|\| **532 \| 2018-07-06**: Andrew Wheeler, a former coal
lobbyist and Deputy Administrator of the EPA since April 2018, succeeds
Scott Pruitt as acting EPA administrator. \|\| **535 \| 2018-07-09**:
President Trump nominates Brett Kavanaugh, a U.S. Appellate Court Judge
on the District of Columbia Circuit, to fill the vacancy on the U.S.
Supreme Court created by the impending retirement of Associate Justice
Anthony Kennedy. \|\| **538 \| 2018-07-12**: President Trump and First
Lady Melania Trump attend a black-tie dinner at Blenheim Palace. \|\|
**539 \| 2018-07-13**: Special counsel Robert Mueller indicts twelve
Russian intelligence officers, alleging that they “engag\[ed\] in a
‘sustained effort’ to hack Democrats’ emails and computer networks”. \|
President Trump holds a bilateral meeting and joint press conference
with British Prime Minister Theresa May at Chequers. President Trump
advises May to “sue the E.U.” during Brexit negotiations. \| President
Trump and First Lady Melania Trump meet Queen Elizabeth II at Windsor
Castle. \|\| **541 \| 2018-07-15**: President Trump remarks during a CBS
interview, “Now you wouldn’t think of the European Union, but they’re a
foe,” in response to a question about the biggest foes of the United
States. \|\| **542 \| 2018-07-16**: President Trump and Russian
President Vladimir Putin participate in a summit at the Presidential
Palace in Helsinki, Finland. At the joint press conference, Trump
reiterates both his faulting of “U.S. foolishness and stupidity” and the
Mueller investigation for the freeze in relations between Russia and the
United States and his refusal to recognize the Russian government’s
interference in the 2016 U.S. elections, despite extensive assessments
by United States intelligence agencies. \| President Trump receives
bi-partisan criticism: prominent Republican senators call his summit
performance “disgraceful”, “shameful”, and “a sign of weakness”; former
CIA Director John Brennan calls it “imbecilic” and “nothing short of
treasonous”. \|\| **543 \| 2018-07-17**: The Treasury Department repeals
the requirement of some non-profit groups, most prominently the National
Rifle Association (NRA), to disclose their donor lists to the Internal
Revenue Service. The rule change is announced whilst the NRA was named
as the “primary avenue of influence” for Maria Butina, a Russian
national charged on July 16 by the national security division of the
Justice Department with conspiracy to act as an agent of the Russian
government within the United States without the requisite notification
to the U.S. Attorney General. The affidavit alleges that Butina (along
with an unnamed business partner, presumed to be Aleksandr Torshin)
“infiltrat\[ed\] organizations having influence in American politics,
for the purpose of advancing the interests of the Russian Federation”.
\| Trump claims that he misspoke in his joint press conference with
Putin the previous day, saying “I don’t see any reason why it would be
Russia” when he intended to say “I don’t see any reason why it wouldn’t
be Russia”:It should have been obvious-I thought it would be obvious-but
I would like to clarify, just in case it wasn’t. In a key sentence in my
remarks, I said the word “would” instead of “wouldn’t”. The sentence
should have been: “I don’t see any reason why I wouldn’t-or why it
wouldn’t be Russia.” So just to repeat it, I said the word “would”
instead of “wouldn’t”. And the sentence should have been-and I thought
it would be maybe a little bit unclear on the transcript or unclear on
the actual video-the sentence should have been: “I don’t see any reason
why it wouldn’t be Russia.” Sort of a double negative. \| Trump’s new
remarks are criticized by some Democratic senators who do not believe he
misspoke and thought his “back-handed retraction” was “too late”. \|\|
**544 \| 2018-07-18**: When asked by a reporter before a Cabinet meeting
whether he believes that the Russian government continues to make
efforts to interfere in American elections, Trump replied, “no”.
However, Sarah Huckabee Sanders (the White House Press Secretary)
disputed that Trump was in fact answering the reporter’s question when
he said “no”, and Trump himself refused to clarify his intent to the
press later in the day. \| The New York Times reports that Trump was
briefed on January 6, 2017, regarding the Russian government’s attempts
to interfere in American elections. Trump “sounded begrudgingly
convinced”, according to the Times’s sources. \| Trump receives a public
request from Russian prosecutors for permission to interrogate eleven
American citizens, including former Amb. Michael McFaul, as part of an
investigation into financial crimes that the Russian government alleges
against American hedge-fund manager Bill Browder. Trump did not
immediately decline the request, with Sarah Huckabee Sanders saying that
Trump is “gonna meet with his team” regarding the request. \|\| **545 \|
2018-07-19**: After a non-binding resolution to oppose permitting
Russian investigators to interrogate any American citizen passes in the
United States Senate by a vote of 98-0, the Trump administration issues
a statement that the request “was made in sincerity by President Putin,
but President Trump disagrees with it”. \| Trump invites Russian
President Vladimir Putin to Washington, D.C., in the fall, according to
a tweet from Sarah Huckabee Sanders. \| Dan Coats (the Director of
National Intelligence) reacts to the news of the Putin invitation in a
manner deemed by White House officials to be “laughing at the
president”, and a senior White House official anonymously says to The
Washington Post that “Coats has gone rogue”. \|\| **546 \| 2018-07-20**:
The New York Times reports that Trump’s long-time lawyer, Michael Cohen,
secretly recorded a phone call in which Trump and Cohen discuss a
September 2016 payment, in the amount of 150,000, by American Media,
Inc. (the owner of the National Enquirer) to Playboy model Karen
McDougal in order to acquire the exclusive rights to her story of her
2006 affair with Trump. The National Enquirer never planned on
publishing McDougal’s story, so the payment (termed a “catch and kill”
payment) effectively silenced McDougal’s story for the duration of the
2016 presidential campaign. The Times also reported that the tape
contains a discussion of a back-payment from Trump to American Media,
Inc.; the reporting directly contradicted Trump’s long-standing claim
that he had no knowledge of the payment to either McDougal or American
Media, Inc. \| Rudy Giuliani, Trump’s legal adviser, comments that the
tape is, in fact, “powerful exculpatory evidence”. Some commentators
conclude that Trump’s legal team, not Cohen’s legal team, had leaked the
tape to the media; the tape had originally been shielded from
prosecutors due to attorney-client privilege, which was waived by
Trump’s legal team. Some commentators speculate that Trump’s legal team
released the tape partly to deny Cohen a bargaining device in potential
plea negotiations involving cooperation with federal investigations. \|
Special counsel Robert Mueller moves to subpoena Kristin Davis, the
prostitution mogul known as the “Manhattan Madam”. Davis had been best
known for her role in the 2008 prostitution scandal involving
then-Governor Eliot Spitzer of New York, but she was also a former
employee of Roger Stone, a Republican political operative and strategist
for Trump. \|\| **548 \| 2018-07-22**: Trump tweets that Russian
interference in the 2016 U.S. elections is “all a big hoax”, appearing
to reverse his position yet again on whether the Russian government
interfered (and continues to attempt to interfere) in U.S. elections. \|
Trump tweets a threat to Iranian President Hassan Rouhani:NEVER, EVER
THREATEN THE UNITED STATES AGAIN OR YOU WILL SUFFER CONSEQUENCES THE
LIKES OF WHICH FEW THROUGHOUT HISTORY HAVE EVER SUFFERED BEFORE. WE ARE
NO LONGER A COUNTRY THAT WILL STAND FOR YOUR DEMENTED WORDS OF VIOLENCE
+ DEATH. BE CAUTIOUS!The threat was the culmination of a weekend of
intense rhetorical exchange between the Trump administration and the
Rouhani administration. Trump’s tweet was in response to Rouhani’s
message that war with Iran would be “the mother of all wars”; Rouhani
also warned Trump to “not play with the lion’s tail, because you will
regret it eternally”. Rouhani’s message was, in turn, in response to a
scathing speech made by Mike Pompeo (the U.S. Secretary of State), which
included an allegation that Rouhani owns a 95 billion hedge fund; Pompeo
also stated that “to the \[Iranian\] regime, prosperity, security, and
freedom for the Iranian people are acceptable casualties in the march to
fulfill the Revolution”, and that “the level of corruption and wealth
among regime leaders shows that Iran is run by something that resembles
the mafia more than a government”. \|\| **549 \| 2018-07-23**: President
Trump publicly considers revoking security clearances for former
top-level officials (including John Brennan, James Clapper, James Comey,
Susan Rice, Andrew McCabe, and Michael Hayden); Trump claims that the
former officials’ public comments about the Special Counsel
investigation are “inappropriate”, and Sarah Huckabee Sanders accused
the former officials of “politicizing and … monetizing their public
service”. \| The Senate confirms Robert Wilkie as the 10th U.S.
Secretary of Veterans Affairs in a vote of 86-9; Wilkie served as an
under-secretary in the U.S. Department of Defense since November 2017
(and previously from 2006 to 2009 under President George W. Bush) and
also served as acting Veterans’ Affairs secretary from March 2018 to May
2018 following David Shulkin’s resignation. \| President Trump launches
“Made in America Week” at the White House by showcasing products made in
all 50 states.\[citation needed\] \|\| **550 \| 2018-07-24**: At a
speech to the annual convention of a veterans’ organization (Veterans of
Foreign Wars) in Kansas City, Trump says that “what you’re seeing and
what you’re reading \[in the media\] is not what’s happening”. Some
observers describe this quote as “Orwellian”. \| The September 2016
tape, the existence of which was revealed on July 20, is published by
CNN on its 9:00 p.m. show, Cuomo Prime Time. The three-minute recording
proves that Trump and his then-lawyer, Michael Cohen, did discuss the
150,000 payment to American Media, Inc., as claimed on July 20.
Moreover, Trump and Cohen can be heard discussing whether to make the
payment in cash; on the recording, Trump appears to suggest a cash
payment, and Cohen appears to dismiss the suggestion. According to The
New York Times, the salient portion of the “sometimes muddled” recording
reads as follows: \| Mr. Cohen is heard telling Mr. Trump that he will
need to set up a company to arrange the payments. \| Mr. Trump then
asked, “What financing?” \| “We’ll have to pay,” Mr. Cohen said. \|
Mr. Trump then appears to say, “Pay with cash.” \| Mr. Cohen then says,
“No, no.” \| The word “check” is uttered, but it is not clear by whom,
and the audio is then cut off. \| \| However, Trump’s legal team
disputes this. \|\| **551 \| 2018-07-25**: Eleven Republican members of
the House Judiciary Committee (all members of the House Freedom Caucus)
file an impeachment resolution against Deputy Attorney General Rod
Rosenstein, claiming that Rosenstein in his role as overseer of the
Special Counsel investigation committed “high crimes and misdemeanors”
in refusing to turn over information relating to the ongoing
investigation to the House Judiciary Committee. \| President Trump holds
a bilateral meeting and joint press conference with European Commission
President Jean-Claude Juncker at the White House.\[citation needed\]
\|\| **552 \| 2018-07-26**: The House Republicans who filed an
impeachment resolution against Deputy Attorney General Rod Rosenstein on
July 26 back down, deciding not to continue with impeachment
proceedings. This decision comes after many high-profile Republicans,
including House Speaker Paul Ryan and U.S. Attorney General Jeff
Sessions, criticize the impeachment resolution and express support for
Rosenstein. \| Trump’s former lawyer, Michael Cohen, claims that Trump
had contemporaneous knowledge of the June 2016 Trump Tower meeting
between Trump campaign officials (including Trump’s son, Don Jr., and
son-in-law, Jared Kushner) and Russian lobbyists, where the Trump
campaign was promised “dirt” on Hillary Clinton. While Trump has
repeatedly denied that he knew that this meeting took place, Cohen
claims that he is prepared to testify to the Special Counsel
investigation that Trump knew in advance of the meeting. Commentators
note that “this revelation, if true, would directly implicate Trump
himself in an effort to conspire with a foreign power to tip the
election to him, and a subsequent effort to cover that up.” Trump tweets
in his denial that “\[it\] sounds to me like someone is trying to make
up stories in order to get himself out of an unrelated jam (Taxi cabs
maybe?).” \| The deadline (imposed on June 26 by Dana Sabraw, a U.S.
District Court Judge for the Southern District of California) elapses to
reunite all migrant families separated by the Trump administration. The
government claims that the deadline has been met, but its court filing
shows that 711 children (about a third of the 2,551 children separated
from their families), whom the government has deemed “ineligible for
reunification”, are still in the custody of the Office of Refugee
Resettlement. \|\| **555 \| 2018-07-29**: Trump tweets a threat to
support a government shutdown if Democratic lawmakers do not vote for
“Border Security, which includes the Wall!” \|\| **556 \| 2018-07-30**:
President Trump holds a bilateral meeting and joint press conference
with Italian Prime Minister Giuseppe Conte at the White House. \| After
President Trump has claimed “no collusion” for months, his legal adviser
Rudy Giuliani says that “I don’t even know if \[colluding with Russia\]
is a crime”. Another Trump adviser, former Gov. Chris Christie of New
Jersey, echoes the sentiment, saying that “collusion is not a crime”.
While there technically is no crime called ‘collusion’ in the U.S. Code,
legal experts agree that ‘collusion’ is an informal shorthand for a
number of similar charges, especially conspiracy, which are in the Code,
and that the difference between ‘collusion’ and ‘conspiracy’ is “just a
word choice”. Giuliani’s and Christie’s claims come on the eve of the
trial of former Trump campaign chair, Paul Manafort. \| Giuliani also
claimed the existence of a previously-unknown June 7, 2016, meeting
between Trump campaign officials and Russian lobbyists preceding the
Trump Tower meeting on June 9, 2016; however, Giuliani later said that
the meeting “never happened”. Asked how he could be sure that the July
26 claim by Trump’s former lawyer Michael Cohen (that Trump had advance
knowledge of the Trump Tower meeting) was false, Giuliani replied,
“Nobody can be sure of anything”. \| President Trump offers to meet
Iranian President Hassan Rouhani with “no preconditions”. This follows a
heated exchange between the Trump administration and Rouhani on July 21
and July 22. \| Robert Wilkie is sworn in as the 10th U.S. Secretary of
Veterans Affairs. \| According to U.S. intelligence agencies, North
Korea continues to construct nuclear missiles capable of reaching the
United States, despite peace talks at the June 12 summit between Trump
and Chairman Kim Jong-un. \|\| **557 \| 2018-07-31**: The trial of
former Trump campaign chair, Paul Manafort, begins in the U.S. \|
District Court for the Eastern District of Virginia. \| Anthony Kennedy
retires as Associate Justice of the U.S. Supreme Court, formalizing a
decision announced on June 27. \| During a rally in Florida, President
Trump defends strict “voter ID” laws by claiming that Americans are
required to show identification to purchase groceries. \|\| **558 \|
2018-08-01**: President Trump tweets that “Attorney General Jeff
Sessions should stop this Rigged Witch Hunt right now, before it
continues to stain our country any further”, the first time Trump has
publicly and explicitly called for the termination of the Special
Counsel investigation. Many observers note that this tweet raises
concerns about possible obstruction of justice, while Rudy Giuliani
(Trump’s legal adviser) claims that Trump intentionally chose the word
“should” because he was expressing an opinion rather than issuing an
order to Sessions;Sarah Huckabee Sanders (the White House Press
Secretary) echoes Giuliani’s sentiments, saying, “It’s not an order.
It’s the president’s opinion.” \|\| **559 \| 2018-08-02**: Sarah
Huckabee Sanders (the White House Press Secretary) calls the press the
“enemy of the people”. \| At a press conference, top national security
officials (Dan Coats, Kirstjen Nielsen, John Bolton, Christopher Wray,
and Paul Nakasone) announce that the administration will “make the
matter of election meddling and securing our election process a top
priority”. The officials also affirm that the Russian government is
attempting to interfere in the U.S. midterm elections, specifically with
“a pervasive messaging campaign by Russia to try to weaken and divide
the United States”. \|\| **560 \| 2018-08-03**: A Justice Department
filing on a case against the American Civil Liberties Union (ACLU)
regarding reunification of separated migrant families argues that it is
the responsibility of the plaintiffs (i.e., the ACLU), not the
government, to use its “considerable resources” to find parents of
separated children whom the government has already deported. The judge
who requested the government filing (Dana Sabraw, a U.S. District Court
Judge for the Southern District of California appointed by President
George W. Bush) calls the government’s slow pace in reuniting the
separated families “unacceptable”, and rejects “100%” the argument that
the responsibility is on the ACLU to reunite the families. \|\| **566 \|
2018-08-09**: The White House director of strategic communications,
Mercedes Schlapp, confirms with Univision that Helen Aguirre Ferre, the
White House director of media affairs for Latino and African-American
news outlets, has resigned from the White House. \|\| **569 \|
2018-08-12**: Two days before her memoir (Unhinged) is released, Omarosa
Manigault, a former White House aide to Trump primarily known for her
prior appearances on The Apprentice, a reality television show formerly
hosted by Trump, releases audio recordings of Trump and John Kelly
(Trump’s White House Chief of Staff) regarding her January 2018
dismissal. Manigault claims that “there are tapes of \[Trump\] using the
N-word repeatedly while filming The Apprentice reality series”. \|\|
**570 \| 2018-08-13**: In a flurry of early-morning tweets, President
Trump describes Omarosa Manigault as “wacky”, “vicious”, “not smart”,
“nasty”, “a loser”, and “a lowlife”, and claims that she “begged
\[Trump\] for a job, tears in her eyes”. \| Prosecutors from the Special
Counsel investigation rest their case in the trial of Paul Manafort. \|
Peter Strzok, an FBI agent and Chief of the Counter-espionage Section
who was removed from Mueller’s Special Counsel investigation upon the
discovery of his anti-Trump texts, is dismissed from the FBI by Deputy
Director David Bowdich. Strzok is notorious amongst right-wing
legislators and media figures who leaked and scrutinized the text
messages which he exchanged with fellow agent Lisa Page and which were
falsely alleged to demonstrate anti-Trump bias that would have
undermined Strzok’s apolitical role as a leading investigator of the
Russian government’s interference in the 2016 U.S. elections. \|
President Trump signs legislation named the John S. McCain National
Defense Authorization Act while not mentioning the Senator’s name. \|\|
**571 \| 2018-08-14**: President Trump tweets that Omarosa Manigault had
been “a crazed, crying lowlife” when he gave her a job at the White
House, describing the appointment as Trump giving Manigault “a break”;
in the same tweet, Trump called Manigault a “dog”. Some commentators
express concern that Manigault, whose official title had been Assistant
to the President and Director of Communications for the Office of Public
Liaison, carrying a taxpayer-funded annual salary of 180,000, had been
hired out of pity as Trump admits to knowing at the time that she was
unqualified for the position. \|\| **572 \| 2018-08-15**: President
Trump unilaterally revokes the security clearance of former CIA Director
John Brennan, citing what Trump alleges to be Brennan’s “erratic”
behavior, “increasingly frenzied commentary”, and his “series of
unfounded and outrageous allegations”; many observers agree that this
action appears to be retaliation for Brennan’s outspokenness on the
possible collusion to interfere in the 2016 elections by the Trump
campaign and the Russian government being investigated the Special
Counsel investigation, especially because Trump did not make an
allegation that Brennan mis-handled or mis-used classified information
that would have warranted the revocation. In an interview with The Wall
Street Journal, Trump directly connected the revocation of Brennan’s
security clearance with his frustration at the ongoing Special Counsel
investigation. \|\| **573 \| 2018-08-16**: Former CIA Director John
Brennan responds to Trump’s unilateral revocation of his security
clearance, contending in a New York Times opinion-editorial, that
“Trump’s ‘no collusion’ claims are hogwash”, and that Trump “revoked
\[Brennan’s\] security clearance to try to silence anyone who would dare
challenge him”. In addition, William McRaven, a navy admiral best known
for his role as special operations commander overseeing the raid that
killed Osama bin Laden, publicly expresses a political position by
authoring an opinion-editorial in The Washington Post in defense of
Brennan; McRaven dares Trump to also revoke his security clearance,
writing:I would consider it an honor if you would revoke my security
clearance as well, so I can add my name to the list of men and women who
have spoken up against your presidency.In response, President Trump
threatens to revoke the security clearances of more former top-level
intelligence officials. Observers draw comparisons between Trump’s list
of officials whose security clearances he threatens to revoke (which
includes James Clapper, James Comey, Michael Hayden, Sally Yates, Susan
Rice, Andrew McCabe, Peter Strzok, Lisa Page, and Bruce Ohr) and Richard
Nixon’s Enemies List. \| Hundreds of newspapers across the United States
publish editorials emphasizing the importance of the freedom of the
press, a right which is guaranteed by the First Amendment. (The
newspapers coordinated the publication date of the editorials, but each
wrote an editorial independently.) The effort is in response to recent
attacks by the Trump administration on the press, especially to combat
the appellation, “enemy of the people”. \|\| **574 \| 2018-08-17**:
President Trump tweets that the military parade scheduled for November
2018 will be postponed due to cost. Trump blames “the local politicians
who run Washington, D.C. (poorly)” of price gouging in reporting the
estimated cost of the parade as 92 million, which covers 50 million for
military equipment and aircraft, and 42 million for municipal costs such
as security.Defense Secretary Jim Mattis accuses the individual writing
the report asserting the 92 million figure of “probably smoking
something that is legal in my state but not in most”.Washington, D.C.
Mayor Muriel Bowser responds by tweeting:Yup, I’m Muriel Bowser, mayor
of Washington DC, the local politician who finally got thru to the
reality star in the White House with the realities (21.6M) of
parades/events/demonstrations in Trump America (sad).OMB Director Mick
Mulvaney says that there were other non-monetary considerations that
factored into the decision to postpone the parade; Mulvaney would not
specify the other “contributing factors”. \|\| **575 \| 2018-08-18**:
The New York Times reports that the White House Counsel, Don McGahn, has
testified for nearly thirty hours in three voluntary interviews with
investigators working on the Special Counsel investigation. According to
the report, Trump and his lawyers allowed McGahn to testify, and did not
ask for a de-briefing of the content of his testimony, which included
the manner in which FBI Director James Comey was dismissed, as well as
other personnel-related matters, including Trump’s “obsession with
putting a loyalist in charge of the \[Special Counsel\] inquiry”. In
response to the report, Trump tweets that “disgraced and discredited Bob
Mueller and his whole group of Angry Democrat Thugs spent over 30 hours
with the White House Counsel, only with my approval, for purposes of
transparency.” \|\| **576 \| 2018-08-19**: In an interview on Meet the
Press, a news program on NBC hosted by Chuck Todd, Trump’s legal adviser
Rudy Giuliani says that “truth isn’t truth”. Giuliani later clarified
that he was “referring to the situation where two people make precisely
contradictory statements, the classic ‘he said, she said’ puzzle”. Many
observers, noting that this is the latest in a sequence of unusual
statements, including Kellyanne Conway’s “alternative facts”, Trump’s
“fake news”, and Trump’s recent claim that “what you’re seeing and what
you’re reading is not what’s happening”, draw comparisons to George
Orwell’s dystopian novel, 1984. \|\| **577 \| 2018-08-20**: President
Trump attacks Bruce Ohr, a current senior Justice Department official,
asking whether he will “ever be fired”. Trump has attacked Ohr numerous
times since August 11, alleging that he and his wife, Nellie, had been
involved both in gathering information for the “Steele dossier” and in
starting the FBI investigation into the Russian government’s
interference in the 2016 U.S. elections. Nellie Ohr worked for Fusion
GPS, the firm which commissioned the dossier, and Bruce Ohr had contact
with Christopher Steele, the author of the dossier, throughout its
production. However, there is no evidence that Ohr had any involvement
with either the FBI investigation or the Special Counsel investigation.
\| The New York Times reports that Trump’s former personal attorney,
Michael Cohen, is under investigation for bank fraud and tax evasion
relating to loans amounting to 20 million, taken for Cohen’s taxi
medallion venture. \|\| **578 \| 2018-08-21**: The first trial of Paul
Manafort, former chair of the Trump campaign, concludes, with the jury
finding Manafort guilty on five counts of tax evasion, two counts of
bank fraud, and one count of failure to disclose a foreign bank account;
Manafort is acquitted on zero counts, and the judge, senior judge T. S.
Ellis III of the U.S. District Court for the Eastern District of
Virginia, declares a mis-trial on the remaining ten counts. \| Michael
Cohen, Trump’s former personal attorney, pleads guilty to five counts of
tax evasion, two counts of campaign finance violations, and one count of
bank fraud. The campaign finance violations relate to Cohen’s
arrangement of payments in 2016 with American Media, Inc. to purchase
the exclusive rights to the stories of Karen McDougal and Stormy
Daniels, regarding their affairs with then-candidate Trump; these are
regarded as “in-kind contributions” to Trump’s campaign, and exceeded
the maximum amount allowable by U.S. campaign finance law. In the court
proceedings, Cohen makes a prepared statement on the charges, describing
the counts in his own words; Cohen implicates Trump on the two counts of
campaign finance violations, saying under oath, and under penalty of
perjury, that he made the illegal campaign contributions “in
coordination with, and at the direction of, a candidate for federal
office \[Trump\]”. Trump denies that he directed Cohen to make the
payments. \|\| **579 \| 2018-08-22**: President Trump makes a video
statement on the death of Mollie Tibbetts. \| The New York State
Department of Taxation and Finance issues a subpoena to Michael Cohen
(Trump’s former personal attorney), as part of its ongoing investigation
into whether the Donald J. Trump Foundation violated New York tax law.
(Note that this is a separate investigation from the lawsuit filed in
June 2018 by the office of the N.Y. Attorney General, Barbara Underwood,
alleging that the Trump Foundation, which is subject to laws concerning
charitable organizations, functioned as “little more than a checkbook
for payments from Mr. Trump or his business to nonprofits, regardless of
their purpose or legality”.) \|\| **580 \| 2018-08-23**: In an interview
with Fox News, President Trump claims that “if I ever got impeached, I
think the market would crash, I think everybody would be very poor”. \|
David Pecker, the CEO of American Media, Inc. (which owns the National
Enquirer magazine), who was, along with Trump, named by Michael Cohen in
his guilty plea as an un-indicted co-conspirator in campaign finance
violations committed in the payments to Stormy Daniels and Karen
McDougal, is granted immunity by federal prosecutors in exchange for his
testimony. A report by the Associated Press indicates that, during the
2016 election, the National Enquirer hid stories to which it had gained
exclusive rights, but which were damaging to Trump, in a safe, as a form
of ‘friendly blackmail’; a National Enquirer reporter told the
Associated Press, “It’s ‘I did this for you, now what can you do for me’
… they \[the National Enquirer\] always got something in return.” \|\|
**584 \| 2018-08-27**: President Trump holds a bilateral meeting with
Kenyan President Uhuru Kenyatta at the White House.\[citation needed\]
\|\| **587 \| 2018-08-30**: President Trump reveals that Jeff Sessions
will remain Attorney General until after the fall 2018 mid-term
elections in November during an interview on Bloomberg. \|\| **591 \|
2018-09-03**: President Trump sarcastically tweets “Good job Jeff …”
following the Justice Department indictments of Duncan Hunter and Chris
Collins. Trump was criticizing Attorney General Jeff Sessions’ handling
of the investigations as supporting the Democratic agenda, adding that
“the Democrats, none of whom voted for Jeff Sessions, must love him
now.” \|\| **592 \| 2018-09-04**: The Senate confirmation hearing for
Brett Kavanaugh begins. \|\| **593 \| 2018-09-05**: The New York Times
publishes an editorial written by an anonymous senior administration
official in the Trump administration which is critical of President
Trump. \| President Trump holds a bilateral meeting with Emir Sabah
Al-Ahmad Al-Jaber Al-Sabah of Kuwait at the White House. \|\| **595 \|
2018-09-07**: Kavanaugh confirmation hearing ends with a vote scheduled
for September 20. Over the course of the hearing, over 200 protesters
were arrested by the Capitol Police. \|\| **599 \| 2018-09-11**:
President Trump speaks at the Flight 93 National Memorial to commemorate
the 17th anniversary of the September 11 attacks. \|\| **600 \|
2018-09-12**: Democrats in the Senate reveal that they have received an
allegation of sexual assault against Kavanaugh. \|\| **605 \|
2018-09-17**: Christine Blasey Ford is identified as the source of the
sexual assault allegation against Kavanaugh. \| President Trump states
that he will not withdraw Kavanaugh’s nomination. \| The Senate
Judiciary Committee delays the confirmation vote to allow Kavanaugh and
Ford to testify. \| President Trump celebrates Hispanic Heritage Month
at the White House.\[citation needed\] \|\| **606 \| 2018-09-18**:
President Trump holds a bilateral meeting and joint press conference
with Polish President Andrzej Duda at the White House. \|\| **611 \|
2018-09-23**: The New Yorker reports that Senate Democrats were informed
of a second allegation of sexual assault against Kavanaugh. \| President
Trump holds a bilateral meeting and dinner with Japanese Prime Minister
Shinzo Abe at Trump Tower.\[citation needed\] \|\| **612 \|
2018-09-24**: President Trump attends the United Nations event on
‘Global Drug Problem’ at the Headquarters of the United
Nations.\[citation needed\] \| President Trump holds a bilateral meeting
with South Korean President Moon Jae-in to sign new revisions into their
free trade agreement. \| President Trump holds bilateral meetings with
Egyptian President Abdel Fattah el-Sisi\[citation needed\] and French
President Emmanuel Macron at the UN General Assembly in New York City.
\|\| **613 \| 2018-09-25**: President Trump holds a bilateral meeting
with Colombian President Ivan Duque Marquez at the UN General Assembly
in New York City. \| President Trump addressed the United Nations
General Assembly at the Headquarters of the United Nations, and drew
laughter from international representatives when he said that the Trump
“administration has accomplished more than almost any administration in
the history of the United States-”so true“. Trump immediately commented
that he had not expected that type of reaction. \|\| **614 \|
2018-09-26**: President Trump holds bilateral meetings with Israeli
Prime Minister Benjamin Netanyahu, Japanese Prime Minister Shinzo Abe,
and British Prime Minister Theresa May at the UN General Assembly in New
York City.\[citation needed\] \| Michael Avenatti tweets the details of
a third accusation against Brett Kavanaugh. \|\| **615 \| 2018-09-27**:
President Trump visits the United States Mission to the United
Nations.\[citation needed\] \| The Senate Judiciary Committee holds a
hearing in which Professor Christine Blasey Ford and Supreme Court
nominee Brett Kavanaugh are questioned about Ford’s allegations. \|\|
**616 \| 2018-09-28**: President Trump holds a bilateral meeting with
Chilean President Sebastian Pinera at the White House.\[citation
needed\] \|\| **619 \| 2018-10-01**: President Trump announces the new
USMCA trade agreement between the United States, Mexico and Canada as a
renegotiation of the former North American Trade Agreement (NAFTA). \|\|
**620 \| 2018-10-02**: The White House corrects the official transcript
from yesterday’s press conference to now include his initial insult of a
reporter. \|\| **621 \| 2018-10-03**: President Trump mocks Senate
Judiciary Committee witness Christine Blasey Ford at a Mississippi
campaign rally. \|\| **623 \| 2018-10-05**: In a vote of 51-49 the
Senate moves to advance the nomination of Brett Kavanaugh as Supreme
Court Justice. \|\| **626 \| 2018-10-08**: President Trump attends the
swearing in of Brett M. Kavanaugh as an Associate Justice of the Supreme
Court in a East Room of the White House ceremony.\[citation needed\]
\|\| **627 \| 2018-10-09**: United Nations Ambassador Nikki Haley
announces her resignation. \|\| **629 \| 2018-10-11**: President Trump
expresses concern over the disappearance of Washington Post journalist
Jamal Khashoggi from the Saudi Arabian embassy in Turkey on October 2.
\|\| **633 \| 2018-10-15**: President Trump suggests”rogue killers" may
be responsible for the murder of Jamal Khashoggi. \|\| **635 \|
2018-10-17**: President Trump says the U.S. is requesting that Turkey
provide audio and video relating to missing Saudi journalist Jamal
Khashoggi, “if it exists”. \| Donald McGahn resigns as White House Chief
Counsel. He will be replaced by Patrick Cipollone. \|\| **637 \|
2018-10-19**: President Trump holds a rally in Mesa, Arizona. \|\| **640
\| 2018-10-22**: President Trump attends a political rally at the Toyota
Center in Houston, Texas, and claims “I’m a nationalist.” \|\| **642 \|
2018-10-24**: President Trump and the White House condemn as “alleged
violent attacks” a number of packages containing “potential explosive
devices” that were addressed to various Democrats and intercepted by the
Secret Service. \|\| **644 \| 2018-10-26**: President Trump attends a
political rally in Charlotte, North Carolina. \|\| **651 \|
2018-11-02**: President Trump attends a campaign rally in Indianapolis,
Indiana. \|\| **652 \| 2018-11-03**: President Trump attends a campaign
rally at Bozeman Yellowstone International Airport in Belgrade, Montana.
\|\| **654 \| 2018-11-05**: President Trump visits Ohio, Indiana and
Missouri to campaign on the eve of the midterm elections. \|\| **655 \|
2018-11-06**: The midterm elections are held with Democrats making
significant gains in the House of Representatives and in state
elections, while Republicans strengthen their slim hold on the Senate.
Gains in the House of Representatives give Democrats the majority, and
the ability to control committees to investigate President Trump and his
administration beginning in January 2019. \|\| **656 \| 2018-11-07**:
Attorney General Jeff Sessions resigns at the request of President Trump
and is replaced by Matthew Whitaker, Sessions’ Chief of Staff. \|
President Trump suspends the access pass of CNN journalist Jim Acosta
after he continues to ask questions and refuses to give up the
microphone. \|\| **658 \| 2018-11-09**: President Trump travels to
France aboard Air Force One. \| President Trump receives a call from
British Prime Minister Theresa May, whom he berates over Iran and
Brexit. \|\| **659 \| 2018-11-10**: President Trump holds a bilateral
meeting with French President Emmanuel Macron at the Elysee Palace. \|
President Trump fails to attend a ceremony at the Aisne Marine American
Cemetery in France. He cites poor weather grounding his helicopter, and
a desire not to disrupt traffic with his potential motorcade. \|\| **660
\| 2018-11-11**: President Trump fails to attend a ceremony with
European leaders in Paris marking the 100th anniversary of the end of
World War I. \| President Trump attends a ceremony at the Arc de
Triomphe with 60 other world leaders. French President Emmanuel Macron
delivers a speech in which he denounces nationalism as a betrayal of
patriotism and warns against ‘old demons coming back to wreak chaos and
death’. This is seen as a rebuke of President Trump and Russian
President Vladimir Putin, who is also in attendance. \| President Trump
returns to Washington where he again misses a ceremony at Arlington
National Cemetery marking the 100th anniversary of the end of World War
I claiming he was unable to do so because he was “extremely busy on
calls for the country”. \|\| **663 \| 2018-11-14**: Media reports that
President Trump has been in a bad mood since the midterm elections due
to the significant Republican losses and is planning to shuffle his
staff including Secretary of Homeland Security Kirstjen Nielsen and
White House Chief of Staff John Kelly. \| President Trump announces
support for the FIRST STEP Act, a bipartisan legislative package of
sentencing and prison overhaul measures. \|\| **666 \| 2018-11-17**:
President Trump visits California to tour the devastation caused by
wildfires. He mistakenly refers to the fire ravaged area as “Pleasure”
rather than Paradise. \|\| **667 \| 2018-11-18**: President Trump sits
for an interview on Fox News Sunday with Chris Wallace. \|\| **668 \|
2018-11-19**: President Trump criticizes Admiral William McRaven, a Navy
Seal and former head of Special Operations Command for not killing Osama
bin Laden sooner. \|\| **669 \| 2018-11-20**: President Trump and First
Lady Melania Trump participate in the National Thanksgiving Turkey
Presentation.\[citation needed\] \| President Trump issues a statement
called extraordinary and remarkable by the media, declaring unwavering
loyalty to Saudi Arabia despite its killing of Khashoggi. \| Details
emerge of attempts by President Trump to order the Justice Department to
prosecute his political enemies, 2016 presidential election opponent
Hillary Clinton and former FBI Director James Comey. \| President
Trump’s lawyers hand in his responses to questions for the Mueller
investigation. \| President Trump defends Ivanka Trump’s use of personal
email for official government business declining to acknowledge
hypocrisy given his calls for Hillary Clinton to be imprisoned for her
use of personal emails during her time as Secretary of State. \| United
States Court of Appeals for the Ninth Circuit, based in San Francisco,
rules against President Trump’s immigration policy. The President lashes
out against the court calling it ‘a lawless disgrace’ and threatening
unspecified retaliation. Chief Justice John G. Roberts issues a rare
statement defending the impartiality of courts. \|\| **670 \|
2018-11-21**: President Trump fires back at Chief Justice Roberts on
Twitter. \|\| **671 \| 2018-11-22**: President Trump spends Thanksgiving
at his Mar-a-Lago estate, visiting a Coast Guard station in Palm Beach.
He uses calls to overseas troops to vent on immigration and trade and to
boast about his own success in a break from non-partisan traditions of
such calls. \| President Trump authorizes troops stationed at the
U.S.-Mexican border to use lethal force if deemed necessary and also
threatens to close the entire southern border with Mexico. \| President
Trump rebuffs the CIA for concluding that the Saudi crown prince was
responsible for the killing of Jamal Khashoggi. \|\| **672 \|
2018-11-23**: The New York Supreme Court rejects a motion by President
Trump to have New York State Attorney General’s lawsuit against the
Trump Foundation dismissed, allowing the case to proceed. The motion was
made on the basis of presidential immunity and political bias. \|\|
**674 \| 2018-11-25**: U.S. Customs and Border Protection temporarily
close all vehicle and pedestrian traffic at the major San Ysidro port of
entry between Tijuana, Mexico and San Diego, California and used tear
gas on migrants and refugees who approached the border fence. \|\| **675
\| 2018-11-26**: President Trump and Vice President Pence speak in
Tupelo and Biloxi, Mississippi, rallies in support of Senator Cindy
Hyde-Smith in the lead up to her run-off election. \| President Trump
defends the use of ‘very safe tear gas’ against migrants. \|\| **677 \|
2018-11-28**: President Trump uses his Twitter account to retweet an
image calling for his political opponents to be imprisoned for treason.
The image includes Rod Rosenstein, his own Deputy Attorney General, and
Robert Mueller. \|\| **678 \| 2018-11-29**: President Trump travels to
Buenos Aires, Argentina, ahead of the G20 summit. He abruptly cancels a
meeting with Russian President Vladimir Putin over Moscow’s capture of
Ukrainian ships and sailors. \| President Trump’s long time lawyer and
fixer Michael Cohen pleads guilty to lying to Congress in relation to
the Mueller Russia investigation. Trump makes a statement to the media
that Cohen was lying to reduce his prison sentence. He further states
that there was nothing wrong with his involvement with an ultimately
unsuccessful personal business deal with Russia during the 2016
presidential election. \|\| **679 \| 2018-11-30**: President Trump
attends the G20 summit hosted by Argentine President Mauricio Macri. \|
President Trump signs the United States-Mexico-Canada Agreement (USMCA)
along with Canadian Prime Minister Justin Trudeau and Mexican President
Enrique Pena Nieto. \| President Trump holds bilateral meetings with
Argentine President Mauricio Macri, Australian Prime Minister Scott
Morrison, Indian Prime Minister Narendra Modi, Japanese Prime Minister
Shinzo Abe and South Korean President Moon Jae-in. \|\| **680 \|
2018-12-01**: President Trump releases a statement on the death of
former President George H. W. Bush and declares December 5, 2018, as a
national day of mourning. \| President Trump holds bilateral meetings
with German Chancellor Angela Merkel and Turkish President Recep Tayyip
Erdogan.\[citation needed\] \| President Trump holds a bilateral meeting
and dinner with Chinese President Xi Jinping, claiming they have reached
an agreement to halt the escalating trade war between the United States
and China. The following Tuesday senior officials play down expectations
and acknowledged that key provisions were not finalized. Trump tweets
that he is a “Tariff Man”, causing stock markets to plunge three
percent. \|\| **682 \| 2018-12-03**: In a series of tweets, President
Trump calls for harsh sentencing of Michael Cohen, following a guilty
plea in cooperation with the Mueller investigation. The president also
praises longtime associate Roger Stone for not cooperating with Mueller.
\| President Trump and First Lady Melania Trump visit the body of late
former President George H. W. Bush, lying in state at the Capitol
Rotunda, to pay their respects. \|\| **683 \| 2018-12-04**: Senate
leaders attend a closed-door security briefing by CIA Director Gina
Haspel and emerge from the meeting to effectively accuse President Trump
of misleading the country over the killing of Jamal Khashoggi. \|
President Trump and First Lady Melania Trump visit former President
George W. Bush and former First Lady Laura Bush at the Blair House, to
offer their condolences to the Bush family. \| Robert Mueller files
court documents for the sentencing of President Trump’s former national
security adviser, General Michael Flynn. Mueller recommends no jail time
based on Flynn’s assistance, including in the Trump-Russia investigation
and several ongoing investigations. \|\| **684 \| 2018-12-05**:
President Trump and First Lady Melania Trump attend the funeral of late
former President George H. W. Bush at Washington National Cathedral. \|
The Washington Post reports that Saudi lobbyists paid for 500 rooms in
President Trump’s Washington DC Hotel following the 2016 election. \|\|
**685 \| 2018-12-06**: President Trump’s former Secretary of State Rex
Tillerson makes public comments criticizing Trump. Trump responds the
following day with an attack on Twitter calling Tillerson ‘lazy’ and
‘dumb as a rock’. \|\| **686 \| 2018-12-07**: President Trump indicates
that he will nominate William P. Barr for the post of Attorney General.
Barr previously served as Attorney General under President George H. W.
Bush. He also indicates that he will nominate Heather Nauert as
Ambassador to the United Nations. \|\| **690 \| 2018-12-11**: President
Trump meets with Democratic Party congressional leaders Nancy Pelosi and
Chuck Schumer in the Oval Office. The meeting is combative, with the
president threatening to shut down the government over funding for the
Mexican border wall. President Trump declares that he would be “proud”
to shut down parts of the government if it were to result in a border
wall. \|\| **691 \| 2018-12-12**: President Trump names Mick Mulvaney,
his budget director, as acting Chief of Staff following the departure of
John Kelly. \| Michael Cohen, President Trump’s former personal lawyer,
is sentenced to three years in prison for tax evasion, violation of
campaign finance laws and deceiving banks and Congress. \|\| **692 \|
2018-12-13**: Federal prosecutors continue to investigate irregularities
by the 2017 Presidential Inaugural Committee. \|\| **694 \|
2018-12-15**: Interior Secretary Ryan Zinke tenders his resignation
letter, effective January 2, 2019. \|\| **697 \| 2018-12-18**: President
Trump agrees to shut down the Donald J. Trump Foundation following an
investigation by New York State Attorney General Barbara Underwood which
found “a shocking pattern of illegality involving the Trump
Foundation-including unlawful coordination with the Trump presidential
campaign, repeated and willful self-dealing, and much more”. \|
President Trump’s Justice Department announces that it will ban bump
stocks. \| President Trump abandons demands for funding for his border
wall, drawing unprecedented criticism from his conservative media
allies. \|\| **698 \| 2018-12-19**: President Trump reassures victory
over ISIS in Syria and announces that U.S. troops will be returned.
Aides, officials and allies are blindsided by the decision, which is
made without any consultation. \| A federal judge blocks the Trump
Administration attempts to deny asylum to domestic violence victims.
\|\| **699 \| 2018-12-20**: Secretary of Defense Jim Mattis announces
his resignation, effective February 28, 2019, with a rebuke of President
Trump’s foreign policy. \| President Trump announces that he intends to
significantly reduce troop numbers in Afghanistan. As with the previous
announcement, consultation is negligible. \| President Trump reverses
again on a federal government shutdown over his border wall, vowing he
will not sign any budget extension bill that does not fund the wall. The
Senate and House are in stalemate with the former voting for no funding
and the latter voting for funding for the wall. \| North Korea announces
that it will not eliminate its nuclear weapons unless the U.S. first
removes nuclear weapons and forces from the region. North Korea further
accuses President Trump of twisting the agreement made between himself
and Kim Jong-un in Singapore on June 22, 2018. \|\| **700 \|
2018-12-21**: President Trump signs the First Step Act into law. The act
is a bipartisan prison and sentencing reform bill with strong bipartisan
support. \| CNN reports that President Trump has twice lashed out at
acting Attorney General Matthew Whitaker over the prosecution of his
former lawyer and fixer Michael Cohen, further reporting that these
events underscore the extent to which the President firmly believes the
Attorney General of the United States should serve as his personal
protector. \|\| **701 \| 2018-12-22**: A government shutdown begins
following the failure of Congress and President Trump to reach a
compromise on border wall funding. \| Brett McGurk, special presidential
envoy for the Global Coalition to Counter the Islamic State of Iraq and
the Levant, resigns effective December 31, 2018, in protest at President
Trump’s decision to pull American troops from Syria. In response,
President Trump wrote that he did not know McGurk and questioned if
McGurk was a “grandstander”. \|\| **702 \| 2018-12-23**: President Trump
has Secretary of State Mike Pompeo tell Secretary of Defense James
Mattis that his departure would be effective January 1. He announces
Patrick M. Shanahan as acting defense secretary. \| While on vacation in
Cabo San Lucas, Mexico, Secretary Mnuchin conducts a series of
individual calls with the CEO’s of America’s six largest banks, to
affirm adequate liquidity and respond to market volatility. \| Day 2 of
the partial government shutdown \|\| **703 \| 2018-12-24**: President
Trump attacks the Federal Reserve via Twitter, saying they are the only
problem in the economy, which is in a significant downturn. Recent
reporting has claimed that the president is seeking to fire the head of
the Federal Reserve for raising interest rates. \| President Trump and
First Lady Melania Trump take calls in the White House for the NORAD
Santa tracker. Trump draws significant media attention when he questions
a 7-year-old caller’s belief in Santa. \| Day 3 of the partial
government shutdown \|\| **704 \| 2018-12-25**: President Trump spends
Christmas with First Lady Melania Trump at the White House, choosing not
to travel to Florida during the government shutdown. \| Day 4 of the
partial government shutdown \|\| **705 \| 2018-12-26**: President and
First Lady Trump make an unannounced Christmas visit to Al Asad Airbase
in Iraq. \| President and First Lady Trump visit American troops
stationed at Ramstein Air Base in Germany. \| Day 5 of the partial
government shutdown \|\| **706 \| 2018-12-27**: Day 6 of the partial
government shutdown \|\| **707 \| 2018-12-28**: Day 7 of the partial
government shutdown \|\| **708 \| 2018-12-29**: Day 8 of the partial
government shutdown \|\| **709 \| 2018-12-30**: Day 9 of the partial
government shutdown \|\| **710 \| 2018-12-31**: Day 10 of the partial
government shutdown \|\| **711 \| 2019-01-01**: James Mattis resigns as
26th United States Secretary of Defense. Deputy Secretary Patrick M.
Shanahan becomes Acting Secretary of Defense. Mattis’ resignation had
been announced December 2018, for the end of February 2019, before being
pushed forward by President Trump. \| Deputy Ambassador to the United
Nations Jonathan Cohen assumes acting duties, following the resignation
of Ambassador Nikki Haley the previous day. \| Day 11 of the partial
government shutdown \|\| **712 \| 2019-01-02**: John F. Kelly resigns as
28th White House Chief of Staff. OMB Director Mick Mulvaney concurrently
becomes Acting Chief of Staff. Kelly’s resignation was announced in
December 2018. \| Ryan Zinke resigns as the 52nd United States Secretary
of the Interior. Deputy Secretary David Bernhardt becomes Acting
Secretary of the Interior. Zinke’s resignation was announced on December
15, 2018. \| The final session of the Republican-controlled House of
Representatives took place. \| Day 12 of the partial government shutdown
\|\| **713 \| 2019-01-03**: Congress convened with a Democratic House
and an expanded Republican majority in the Senate. \| Nancy Pelosi is
elected Speaker of the United States House of Representatives for a
second tenure. \| Day 13 of the partial government shutdown \|\| **714
\| 2019-01-04**: President Trump considers declaring a national
emergency on the southern border in order to bypass Congress on the
issue of a border wall. \| Day 14 of the partial government shutdown
\|\| **715 \| 2019-01-05**: Day 15 of the partial government shutdown
\|\| **716 \| 2019-01-06**: Day 16 of the partial government shutdown
\|\| **717 \| 2019-01-07**: President Trump announces a prime time
televised address on border security for the following day. \| Day 17 of
the partial government shutdown \|\| **718 \| 2019-01-08**: President
Trump addresses the nation on prime-time television concerning the
ongoing federal government shutdown.\[citation needed\] \| Day 18 of the
partial government shutdown \|\| **719 \| 2019-01-09**: President Trump
abruptly walks out of a meeting with Democratic leaders. \| Day 19 of
the partial government shutdown \|\| **720 \| 2019-01-10**: President
Trump visits McAllen, Texas, along the southern border and meets with
Border Patrol personnel. \| Secretary of the Treasury Steven Mnuchin
gives Congress a classified briefing about his decision to lift
sanctions on companies linked to Russian oligarch Oleg Deripaska. \| Day
20 of the partial government shutdown \|\| **721 \| 2019-01-11**: Day 21
of the partial government shutdown \|\| **722 \| 2019-01-12**: The
partial government shutdown enters its 22nd day, becoming the longest
government shutdown in U.S. history after passing the United States
federal government shutdowns of 1995-1996. \|\| **723 \| 2019-01-13**:
Day 23 of the partial government shutdown \|\| **724 \| 2019-01-14**:
President Trump entertains the Clemson Tigers, 2018 College Football
Playoff National Champions, at the White House with a menu of various
fast foods. \| President Trump travels to New Orleans to address the
American Farm Bureau. \| Day 24 of the partial government shutdown \|\|
**725 \| 2019-01-15**: William P. Barr undergoes his confirmation
hearing for the position of Attorney General. \| Trump Administration
calls on some FAA and IRS furloughed employees to return to work to
provide air safety and to implement the upcoming tax filing season. \|
Day 25 of the partial government shutdown \|\| **726 \| 2019-01-16**:
Day 2 of William Barr’s confirmation hearing \| Speaker Pelosi sends a
letter to President Trump that suggests he either reschedule his 2019
State of the Union Address or submit a written State of the Union to
Congress instead of a televised oral speech, citing fears of security
concerns regarding unpaid Secret Service members as a consequence of the
government shutdown. \| President Trump meets in the White House with
rank and file House Democrats to discuss the shutdown. \| Day 26 of the
partial government shutdown \|\| **727 \| 2019-01-17**: President Trump
sends a letter to Speaker Pelosi, postponing her planned trips to
Brussels, Egypt and Afghanistan, a move which is seen by both Democrats
and Republicans as an indirect response to her letter requesting that
the State of the Union Address be rescheduled. \| A report by BuzzFeed
News journalists Jason Leopold and Anthony Cormier is released, alleging
that President Trump directed his former attorney Michael Cohen to lie
to Congress about their Moscow Tower Project. The report further alleges
that Cohen did not reveal this to the Mueller investigation himself, but
rather confirmed it when prompted with evidence such as text and e-mail
exchanges between implicated parties. \| President Trump, alongside Vice
President Mike Pence and Acting Secretary of Defense Patrick M.
Shanahan, visits The Pentagon to address the Missile Defense Review of
2019. In his speech, Trump calls for missile defense in space via a
Space Force as well as reiterating North Korea’s status as an
“extraordinary threat”. \| Day 27 of the partial government shutdown
\|\| **728 \| 2019-01-18**: President Trump and Secretary of State Mike
Pompeo meet with North Korea’s lead negotiator Kim Yong-chol in
Washington, D.C., to discuss denuclearization and preparations for a
second meeting with Kim Jong-un. \| The special counsel’s office issues
a rare statement in response to the report by BuzzFeed News regarding
Michael Cohen’s Congressional testimony by clarifying that it is
inaccurate in its assessment. \| Day 28 of the partial government
shutdown \|\| **729 \| 2019-01-19**: President Trump again delivers
remarks regarding the border and the ongoing shutdown, inviting
Democrats to come to the negotiating table after listing topics of
compromise such as DACA and temporary protected status in exchange for a
border wall while bringing an end to the government shutdown. However,
Democrats seem reluctant to accept this proposition. \| Day 29 of the
partial government shutdown \|\| **730 \| 2019-01-20**: The third year
of the Trump presidency begins \| Day 30 of the partial government
shutdown \|\| **731 \| 2019-01-21**: President Trump and Vice President
Pence make a visit to the Martin Luther King Jr. Memorial to pay tribute
to the late Martin Luther King Jr. on Martin Luther King Jr. Day. \| The
Supreme Court rules that the Trump administration is allowed to limit
military service by transgender people. The court’s five conservative
justices, Chief Justice John Roberts and Justices Samuel Alito, Neil
Gorsuch, Brett Kavanaugh and Clarence Thomas, support the exclusion of
transgender men and women. \| Day 31 of the partial government shutdown
\|\| **732 \| 2019-01-22**: Day 32 of the partial government shutdown
\|\| **733 \| 2019-01-23**: President Trump sends a letter to Speaker
Pelosi stating that he intends to move forward with the planned date of
January 29 for his State of the Union Address. Pelosi blocks his attempt
at an address until the government is reopened, making Trump the first
President in U.S. history to be uninvited to a State of the Union
Address. President Trump responds to this by announcing, via Twitter,
that he will not seek an alternative route for his 2019 State of the
Union Address and will instead comply with Speaker Pelosi’s condition of
having the government reopened before going any further. \| Michael
Cohen requests rescheduling his testimony before Congress, citing
increased threats against him and his family by President Trump and his
attorney, Rudy Giuliani. This request is denied by both the House
Oversight Committee and House Intel Committee. \| President Trump and
Vice President Pence officially recognize Juan Guaido as the interim
President of Venezuela as unrest in the country continues to unfold due
to Nicolas Maduro’s refusal to concede. \| Day 33 of the partial
government shutdown \|\| **734 \| 2019-01-24**: Both Democratic and
Republican bills to end the government shutdown fail in the Senate. \|
Day 34 of the partial government shutdown \|\| **735 \| 2019-01-25**:
Roger Stone, a former adviser to President Trump, is indicted by the
Mueller investigation and then arrested by the FBI at his Florida home
on charges of obstruction, witness tampering and making false
statements. He is later released on a 250,000 bond and stripped of his
passport. \| The FAA delays flights at the LaGuardia Airport in New York
City, and multiple other major airports, due to safety concerns from
staffing shortages as a consequence of the ongoing shutdown. \|
President Trump, from the Rose Garden, says he and Congressional leaders
Mitch McConnell and Chuck Schumer have agreed upon a three-week stop-gap
spending deal, which does not contain funding for a wall on the southern
border, in order to temporarily end the government shutdown. In
addition, he states that, if no deal for a border wall is reached within
those three weeks, he will announce a national emergency on the southern
border. \| Speaker Pelosi says President Trump’s State of the Union
Address will be rescheduled from January 29 to a later date. \| The
partial government shutdown ends on its 35th day. \|\| **738 \|
2019-01-28**: The United States Secretary of Homeland Security Kirstjen
Nielsen, Acting Attorney General Matthew Whitaker, Commerce Secretary
Wilbur Ross, and FBI Director Christopher Wray announce 23 criminal
charges (including financial fraud, money laundering, conspiracy to
defraud the United States, theft of trade secret technology, provided
bonus to workers who stole confidential information from companies
around the world, wire fraud, obstruction of justice and sanctions
violations) against Chinese tech giant Huawei and its CFO Meng Wanzhou.
\|\| **742 \| 2019-02-01**: President Trump announces he is withdrawing
the United States from the Intermediate-Range Nuclear Forces Treaty,
accusing Russia of non-compliance. \|\| **746 \| 2019-02-05**: President
Trump delivers his second official State of the Union Address. \| A
fundraising effort by Trump’s 2020 campaign in the days leading to the
address and on the day of the address raised 2.4 million from 76,000
donors. His campaign displayed names of donors on a live streaming
broadcast of the event on Donald Trump’s Facebook page. \|\| **748 \|
2019-02-07**: President Trump speaks at the National Prayer Breakfast.
\|\| **752 \| 2019-02-11**: President Trump holds a rally in El Paso,
Texas. \|\| **754 \| 2019-02-13**: President Trump holds a bilateral
meeting with Colombian President Ivan Duque Marquez at the White House.
\|\| **755 \| 2019-02-14**: The Senate confirms William Barr as the 85th
U.S. Attorney General in a vote of 54-45. \|\| **756 \| 2019-02-15**:
President Trump declares a national emergency in order to secure
sufficient funds to construct a physical barrier along the Southern
border. \|\| **759 \| 2019-02-18**: President Trump holds a rally in
Miami, Florida where he addresses the ongoing leadership crisis in
Venezuela and shows his support for Venezuelan Opposition Leader Juan
Guaido. \|\| **761 \| 2019-02-20**: President Trump holds a bilateral
meeting with Austrian Chancellor Sebastian Kurz at the White House. \|\|
**765 \| 2019-02-24**: President Trump attends the National Governors
Association dinner. \|\| **768 \| 2019-02-27**: President Trump holds a
bilateral meeting with Vietnamese President Nguyen Phu Trong and
Vietnamese Prime Minister Nguyen Xuan Phuc. \| President Trump and North
Korean Leader Kim Jong-un participate in a summit at the Metropole Hotel
in Hanoi, Vietnam. \|\| **769 \| 2019-02-28**: President Trump and North
Korean Leader Kim Jong-un participate in a summit at the Metropole Hotel
in Hanoi, Vietnam. However, the talks end early without any nuclear
weapons deals or peace accords produced. \|\| **771 \| 2019-03-02**:
President Trump gives a speech in Oxon Hill, Maryland to the 2019
Conservative Political Action Conference. \|\| **773 \| 2019-03-04**:
President Trump entertains the North Dakota State Bison, 2018 College
Football Playoff National Champions, at the White House with a menu of
various fast foods. \|\| **776 \| 2019-03-07**: President Trump holds a
bilateral meeting with Czech Prime Minister Andrej Babis at the White
House. \|\| **783 \| 2019-03-14**: President Trump holds a bilateral
meeting with Taoiseach Leo Varadkar of Ireland at the White House. \|\|
**788 \| 2019-03-19**: President Trump holds a bilateral meeting and
joint press conference with Brazilian President Jair Bolsonaro at the
White House. \|\| **789 \| 2019-03-20**: President Trump visits Lima
Army Tank Plant. \|\| **791 \| 2019-03-22**: Special Counsel Robert
Mueller finishes his investigation into Russian interference in the 2016
presidential election and the alleged relationship between Donald Trump
and Russia and submits his report to Attorney General William Barr. \|
President Trump meets with the leaders of five Caribbean countries in
Mar-a-Lago, Florida: Dominican President Danilo Medina, Haitian
President Jovenel Moise, Jamaican Prime Minister Andrew Holness, Saint
Lucian Prime Minister Allen Chastanet and Bahamian Prime Minister Hubert
Minnis. \|\| **793 \| 2019-03-24**: A four-page summary of the Mueller
Report was released to Congress and found that President Trump did not
collude with the Russians to win the 2016 presidential election and, in
the opinion of AG Barr, the issue of whether obstruction of justice was
committed was found to be inconclusive. \|\| **794 \| 2019-03-25**:
President Trump holds a bilateral meeting and joint press conference
with Israeli Prime Minister Benjamin Netanyahu at the White House. \|
President Trump signs a presidential proclamation to officially
recognize Israel’s sovereignty over the Golan Heights. \|\| **795 \|
2019-03-26**: Congress fails to obtain the 2/3 vote needed to overturn
President Trump veto in regard to the national emergency which was
declared on February 15. \|\| **796 \| 2019-03-27**: President Trump
meets with Fabiana Rosales, wife of Venezuelan Opposition Leader Juan
Guaido, at the White House. \| President Trump participates in an
interview with author Kate Andersen Brower, who was working on the book,
“Team of Five: The President’s Club in the Age of Trump”\[citation
needed\] \|\| **797 \| 2019-03-28**: President Trump holds a rally in
Grand Rapids, Michigan. \|\| **802 \| 2019-04-02**: President Trump
holds a bilateral meeting with NATO Secretary General Jens Stoltenberg
at the White House. \|\| **804 \| 2019-04-04**: President Trump
threatens to close the United States-Mexico border within one year if
Mexico does not stop the “massive amounts of drugs” coming into the
United States. \|\| **805 \| 2019-04-05**: President Trump visits
Calexico, California, along the southern border and meets with Border
Patrol personnel. \| President Trump withdraws his nomination of Ronald
Vitiello to be the director of Immigration and Customs Enforcement. \|\|
**806 \| 2019-04-06**: President Trump speaks at the Republican Jewish
Coalition in Las Vegas, Nevada. \|\| **807 \| 2019-04-07**: President
Trump announces in a tweet that Department of Homeland Security
Secretary Kirstjen Nielsen is resigning. \|\| **808 \| 2019-04-08**:
Secret Service director Randolph Alles to leave his position in May at
President Trump’s request. \|\| **809 \| 2019-04-09**: President Trump
holds a bilateral meeting with Egyptian President Abdel Fattah el-Sisi
at the White House. \| President Trump has installed senior White House
adviser Stephen Miller to be in charge of the administration’s
immigration policy. \|\| **810 \| 2019-04-10**: Kevin McAleenan assumes
the role of Acting Secretary of Homeland Security. \|\| **811 \|
2019-04-11**: President Trump holds a bilateral meeting with South
Korean President Moon Jae-in at the White House. \| The Senate confirms
David Bernhardt as the 53rd U.S. Secretary of the Interior in a vote of
56-41. \| Secretary of the Treasury Department Steve Mnuchin advised the
House Ways and Means Committee that he has “serious issues” with the
committees request for recent Donald Trump tax returns. \|\| **812 \|
2019-04-12**: President Trump confirms reports that he is considering
the release of detained undocumented immigrants into “sanctuary cities”.
\| Linda McMahon’s resignation becomes effective as head of the Small
Business Administration. President Trump made the original announcement
on March 29, 2019. \|\| **815 \| 2019-04-15**: Attorney General William
Barr issues an order directing immigration judges to deny posting of
bail by asylum seekers. \|\| **816 \| 2019-04-16**: President Trump uses
the second veto of his Administration on a bipartisan resolution to end
American involvement in the military campaign in Yemen. Congress had
earlier voted to invoke the War Powers Act of 1973. \|\| **818 \|
2019-04-18**: Attorney General William Barr and Deputy Attorney General
Rod Rosenstein hold a press conference on the Mueller Report and, soon
after, release it to Congress and the American public. \|\| **822 \|
2019-04-22**: President Trump and First Lady Melania Trump host the
White House Easter Egg Roll. \|\| **826 \| 2019-04-26**: President Trump
and Vice President Pence speak at National Rifle Association’s annual
convention in Indianapolis, Indiana. \| President Trump holds a
bilateral meeting with Japanese Prime Minister Shinzo Abe at the White
House. \|\| **827 \| 2019-04-27**: President Trump and Japanese Prime
Minister Shinzo Abe play golf together at the Trump National Golf Club.
\| President Trump holds a rally in Green Bay, Wisconsin. \|\| **829 \|
2019-04-29**: President Trump entertains the Baylor Lady Bear, 2019
College Basketball Playoff National Champions, at the White House with a
menu of various fast foods. \| Deputy Attorney General Rod Rosenstein
submits a letter of resignation effective May 11. \|\| **831 \|
2019-05-01**: James M. Murray is sworn in as Director of the United
States Secret Service. \| Attorney General William Barr appeared before
the Senate Judiciary Committee, answering questions about the Mueller
Report. \|\| **832 \| 2019-05-02**: President Trump speaks at the
National Day of Prayer service in the Rose Garden. \|\| **833 \|
2019-05-03**: President Trump holds a bilateral meeting with Slovak
Prime Minister Peter Pellegrini at the White House. \|\| **836 \|
2019-05-06**: President Trump presents the Commander-in-Chief’s Trophy
to the Army Black Knights football team. \| President Trump presents the
Presidential Medal of Freedom to golfer Tiger Woods. \| Treasury
Secretary Steven Mnuchin fails to meet the House Ways and Means
Committee deadline to provide President Trump’s tax returns. \|\| **838
\| 2019-05-08**: President Trump asserts executive privilege over the
full Mueller Report. \| President Trump holds a rally in Panama City
Beach, Florida. \| The House Judiciary Committee, in a 24-16 vote, moves
to hold Attorney General William Barr in contempt of Congress for
failing to deliver the unredacted version of the Mueller report. \|
House Intelligence Committee issues a subpoena to the Justice Department
for all “counterintelligence and foreign intelligence” collected for the
pre-redacted version of special counsel Robert Mueller’s report. \|\|
**839 \| 2019-05-09**: President Trump entertains the Boston Red Sox,
2018 World Series Champions, at the White House. However, manager Alex
Cora and several star players chose not to attend. \|\| **840 \|
2019-05-10**: The Trump Administration raises tariffs on 200 billion
worth of Chinese imports. \| House Ways and Means Committee chairman
Richard Neal subpoenas the Treasury Department and the Internal Revenue
Service for the tax returns of President Trump. \|\| **841 \|
2019-05-11**: Effective day of Deputy Attorney General Rod Rosenstein’s
resignation. \|\| **843 \| 2019-05-13**: President Trump holds a
bilateral meeting with Hungarian Prime Minister Viktor Orban at the
White House. \|\| **844 \| 2019-05-14**: President Trump visits Cameron
LNG Export Facility. \|\| **846 \| 2019-05-16**: President Trump holds a
bilateral meeting with Swiss President Ueli Maurer at the White House.
\| President Trump proposes a new immigration plan. \|\| **847 \|
2019-05-17**: President Trump speaks at the National Association of
REALTORS Legislative Meetings and Trade Expo. \| The Trump
administration rejects a Democratic subpoena by the House of
Representatives for President Trump’s tax returns. \|\| **850 \|
2019-05-20**: A federal judge from the DC District Court denies
President Trump’s bid to quash a House Oversight Committee subpoena for
years of his financial records from his accounting firm. The judge also
declined a request by the president’s lawyers to stay his order pending
their appeal. \| The Department of Justice moves to block former White
House counsel Don McGahn from testifying to Congress about the Mueller
report citing the separation of powers. \| President Trump holds a rally
in Montoursville, Pennsylvania. \|\| **852 \| 2019-05-22**: President
Trump leaves a meeting on infrastructure with senior Democrats after
only three minutes. Shortly afterwards, he holds a surprise press
conference in the Rose Garden. \|\| **854 \| 2019-05-24**: President
Trump travels to Japan aboard Air Force One for a four-day state visit.
\|\| **855 \| 2019-05-25**: President Trump arrives in Tokyo, Japan. \|
The New York Times reported the White House never followed through with
stripping John Brennan of his security clearance, as Trump had asserted
he had on August 15, 2018. \|\| **856 \| 2019-05-26**: President Trump
meets with Japanese Prime Minister Shinzo Abe at Mobara Country Club. \|
President Trump and Japanese Prime Minister Shinzo Abe attend a sumo
tournament. \|\| **857 \| 2019-05-27**: President Trump holds a joint
press conference with Japanese Prime Minister Shinzo Abe at the Akasaka
Palace. \| President Trump meets with Emperor Naruhito and Empress
Masako at the Tokyo Imperial Palace. \|\| **858 \| 2019-05-28**:
President Trump boards the USS Wasp (LHD-1) in Yokosuka, Japan. \|
President Trump departs Japan. \|\| **859 \| 2019-05-29**: Robert
Mueller announces his resignation as Special Counsel in a press
conference and speaks publicly about his report. \|\| **860 \|
2019-05-30**: President Trump delivers the commencement address at the
U.S. Air Force Academy in Colorado Springs, Colorado. \|\| **862 \|
2019-06-01**: President Trump announces via tweet that White House
counsel Emmet Flood will be leaving his post on June 14. \|\| **863 \|
2019-06-02**: President Trump delivers an evening speech at the Ford’s
Theater’s annual fundraising gala. \| President Trump travels to the
United Kingdom aboard Air Force One for a three-day state visit. \|\|
**864 \| 2019-06-03**: President Trump arrives in London, United
Kingdom. \| President Trump and First Lady Melania Trump meet Queen
Elizabeth II at Buckingham Palace. \| President Trump lays a wreath at
the Tomb of the Unknown Warrior in Westminster Abbey. \| President Trump
and First Lady Melania Trump attends a state banquet hosted by Queen
Elizabeth II at Buckingham Palace. \| The Chairman of the White House’s
Council of Economic Advisers, Kevin Hassett, announces he will soon be
leaving his post. \|\| **865 \| 2019-06-04**: President Trump holds a
bilateral meeting and joint press conference with British Prime Minister
Theresa May at 10 Downing Street. \| President Trump and First Lady
Melania Trump hosts a black-tie dinner at Winfield House. \| Hope Hicks,
a former aide to President Trump, and Annie Donaldson, a former McGahn
aide, are instructed by the White House not to comply with House
Judiciary Committee subpoenas. \|\| **866 \| 2019-06-05**: President
Trump holds a bilateral meeting with German Chancellor Angela Merkel. \|
President Trump attends the 75th anniversary of D-Day commemorative
ceremonies in Portsmouth. \| President Trump arrives in Shannon,
Ireland. \| President Trump holds a bilateral meeting with Irish
Taoiseach Leo Varadkar. \|\| **867 \| 2019-06-06**: President Trump
arrives in Caen, France. \| President Trump attends the 75th anniversary
of D-Day memorial ceremonies in Normandy. \| President Trump holds a
bilateral meeting with French President Emmanuel Macron at the
Prefecture of Calvados. \| President Trump returns to Shannon, Ireland.
\|\| **868 \| 2019-06-07**: President Trump drops threats of tariffs
against Mexico after the United States reaches a deal with Mexico over
Latin American immigration. \|\| **871 \| 2019-06-10**: President Trump
presents the Borg-Warner trophy to the 103rd Indianapolis 500 Champion
Team. \|\| **872 \| 2019-06-11**: President Trump visits Southwest Iowa
Renewable Energy Facility. \|\| **873 \| 2019-06-12**: President Trump
holds a bilateral meeting and joint press conference with Polish
President Andrzej Duda at the White House. \|\| **874 \| 2019-06-13**:
White House Press Secretary Sarah Sanders announces that she will be
leaving her role on June 30. \|\| **875 \| 2019-06-14**: The Office of
Special Counsel recommends Trump aide Kellyanne Conway be “removed from
service” for violating the Hatch Act, which bans federal employees from
political activity. \|\| **879 \| 2019-06-18**: President Trump holds a
rally and formally launches his 2020 reelection campaign in Orlando,
Florida. During the rally President Trump vowed if “elected to a second
term we will cure cancer and ends AIDS’ and”come up with the cures to
many, many problems, to many, many diseases“. \| President Trump
withdraws the nomination of Patrick Shanahan to be Secretary of Defense
and names Mark Esper as his replacement. \|\| **880 \| 2019-06-19**:
President Trump presents the Presidential Medal of Freedom to economist
Arthur Laffer. \| EPA administrator Andrew Wheeler announces a roll-back
of the Clean Power Plan. States will now be allowed to set their own
carbon emissions standards for coal-fired power plants. EPA authority on
carbon emissions will be limited going forward. \|\| **881 \|
2019-06-20**: President Trump holds a bilateral meeting with Canadian
Prime Minister Justin Trudeau at the White House. \|\| **882 \|
2019-06-21**: President Trump warns Iran after its Revolutionary Guard
acknowledges shooting down an American drone in the Strait of Hormuz.
Iran claims the drone”violated Iranian airspace“, while U.S. military
claims the drone was shot down over”international airspace" and the
action was “an unprovoked attack on a U.S. surveillance asset”. \|
President Trump and First Lady Melania Trump hosts the second
congressional picnic in the White House South Lawn. \|\| **883 \|
2019-06-22**: President Trump announces that he will delay ICE raids on
immigrants living illegally in 10 major cities by two weeks to allow
Congress to develop a solution for the United States-Mexico border
problem. \|\| **885 \| 2019-06-24**: President Trump announces
retaliatory sanctions on Iran in response to Iran’s actions in taking
down a United States military drone on June 20. \|\| **886 \|
2019-06-25**: President Trump names Stephanie Grisham as the next White
House Press Secretary. \| Diplomatic Protocol Chief Sean Lawler is
suspended prior to the G-20 summit. \| President Trump presents the
Medal of Honor to Army Staff Sergeant David Bellavia. \|\| **887 \|
2019-06-26**: President Trump travels to Asia for a four-day trip to
visit foreign leaders at the 2019 G20 Summit in Osaka, Japan from June
28 to June 29. \| Robert Mueller announces he will testify before the
House Intelligence Committee and the Judiciary Committee in public
hearings to be held on July 17. \| EPA official William Wehrum resigns
amid claims of possible ethics violations. \| Presidential aide
Kellyanne Conway fails to appear at a House Oversight Committee meeting
and will be subpoenaed about her possible violations of the Hatch Act.
\|\| **888 \| 2019-06-27**: Mark Morgan is picked to take over the U.S.
Border Patrol and Matt Albence will return as acting director of ICE. \|
Supreme Court blocks a citizenship question from being included in the
2020 census and says “the administration provided a contrived
justification” for including it. \| President Trump arrives in Osaka,
Japan. \| President Trump holds a bilateral meeting and dinner with
Australian Prime Minister Scott Morrison. \|\| **889 \| 2019-06-28**:
President Trump attends the G20 summit hosted by Japanese Prime Minister
Shinzo Abe. \| President Trump holds bilateral meetings with Brazilian
President Jair Bolsonaro, Japanese Prime Minister Shinzo Abe, Indian
Prime Minister Narendra Modi, German Chancellor Angela Merkel and
Russian President Vladimir Putin. \|\| **890 \| 2019-06-29**: President
Trump holds a bilateral meeting with Chinese President Xi Jinping,
declaring a truce in the trade war. \| President Trump holds a bilateral
meeting Turkish President Recep Tayyip Erdogan. \| President Trump
arrives in Seoul, South Korea. \| Asked about Putin’s comment that
“western-style liberalism is obsolete,” Trump replied “it’s so sad to
look at what’s happening in San Francisco and a couple of other cities
which are run by an extraordinary group of liberal people. I don’t know
what they’re thinking.” \|\| **891 \| 2019-06-30**: President Trump
holds a bilateral meeting and joint press conference with South Korean
President Moon Jae-in at the Blue House. \| President Trump visits the
Korean Demilitarized Zone (DMZ), accompanied by South Korean President
Moon Jae-in. \| President Trump briefly walks into the northern side of
the Joint Security Area of the Korean Demilitarized Zone (DMZ),
accompanied by North Korean Leader Kim Jong-Un and becomes the first
sitting U.S. President to enter North Korea. \| President Trump returns
to the southern side of the Joint Security Area of the Korean
Demilitarized Zone (DMZ) with North Korean Leader Kim Jong-un. \|
President Trump participate in a DMZ summit with South Korean President
Moon Jae-in and North Korean Leader Kim Jong-un at the Inter-Korean
Freedom House on the southern side of the Joint Security Area of the
Korean Demilitarized Zone (DMZ). \| President Trump holds a bilateral
meeting with North Korean Leader Kim Jong-un at the Inter-Korean Freedom
House. \|\| **892 \| 2019-07-01**: White House Communications Adviser
Mercedes Schlapp announces leaving the Trump Administration and joining
the Trump 2020 Campaign. \|\| **893 \| 2019-07-02**: President Trump
nominates Judy Shelton and Christopher Waller to fill the last two
vacant seats on the Federal Reserve’s Board of the Governors. \|\| **895
\| 2019-07-04**: President Trump hosts military personnel and their
families for a picnic and fireworks show at the Lincoln Memorial as part
of Independence Day celebrations. \| President Trump’s 2019 Salute to
America occurs on Independence Day in Washington, D.C., in addition to
other events. \|\| **900 \| 2019-07-09**: President Trump holds a
bilateral meeting with Emir Tamim bin Hamad Al Thani of Qatar at the
White House. \|\| **902 \| 2019-07-11**: President Trump speaks to
attendees at the President’s Social Media Summit. \|\| **903 \|
2019-07-12**: Secretary of Labor Alex Acosta resigns amid controversy
surrounding the non-prosecution agreement he made with Jeffrey Epstein
as the United States attorney for the Southern District of Florida. \|
President Trump names Patrick Pizzella as acting secretary of labor to
replace Alex Acosta, following the latter’s resignation. \|\| **905 \|
2019-07-14**: President Trump tweets that progressive Democratic
congresswomen should “go back and help fix the totally broken and crime
infested places from which they came”, drawing widespread criticism,
even from some Republicans. \|\| **906 \| 2019-07-15**: President Trump
launches “Made in America Week” at the White House by showcasing
products made in all fifty states. \|\| **907 \| 2019-07-16**: President
Trump denies that his previous tweets made towards several Democratic
congresswomen were in any way racist. \|\| **908 \| 2019-07-17**:
President Trump holds a meeting with survivors of religious persecution
with the United States ambassador-at-large for international religious
freedom, Sam Brownback. Notable participants include Pastor Andrew
Brunson and Nobel Peace Prize winner Nadia Murad. \| President Trump
holds a rally in Greenville, North Carolina. \| The House of
Representatives votes to hold Attorney General William Barr and Commerce
Secretary Wilbur Ross in contempt over an administration decision to add
a citizenship question to the 2020 census. \|\| **909 \| 2019-07-18**:
President Trump holds a bilateral meeting with Dutch prime minister Mark
Rutte at the White House. \| President Trump claims he did in fact try
to stop the crowds chants and “was unhappy” with the chants of “send her
back” from his supporters during the Greensville rally on July 17. \|\|
**910 \| 2019-07-19**: President Trump meets with Apollo 11 astronauts
Buzz Aldrin and Michael Collins. \|\| **913 \| 2019-07-22**: President
Trump holds a bilateral meeting with Pakistani prime minister Imran Khan
at the White House. \|\| **914 \| 2019-07-23**: The Senate confirms Mark
Esper as the 27th U.S. secretary of defense in a vote of 90-8. \|\|
**915 \| 2019-07-24**: Former special counsel Robert Mueller testifies
before the House Judiciary Committee and the House Intelligence
Committee on the Mueller Report. \|\| **916 \| 2019-07-25**: During a
phone conversation with the newly elected Ukrainian president Volodymr
Zelensky, President Trump repeatedly presses him to open an
investigation into Hunter Biden, the son of potential 2020 presidential
candidate and former vice president Joe Biden. \|\| **917 \|
2019-07-26**: The Supreme Court rules in a 5-4 decision that President
Trump may use military funding for construction of the border wall. \|\|
**918 \| 2019-07-27**: President Trump draws criticism for his tweet
describing Congressman Elijah Cummings’ Baltimore, Maryland, district as
a “disgusting, rat and rodent infested mess”. \|\| **919 \|
2019-07-28**: President Trump names Congressman John Ratcliffe as
Director of National Intelligence. \| Three people are killed and 15
injured at the Gilroy, California, Garlic Festival. The suspect, Santino
William Legan, is shot dead by police. \|\| **920 \| 2019-07-29**:
President Trump signs H.R. 1327, the September 11th Victim Compensation
Fund. \|\| **922 \| 2019-07-31**: President Trump holds a bilateral
meeting with Mongolian president Khaltmaagiin Battulga at the White
House. \|\| **923 \| 2019-08-01**: President Trump holds a rally in
Cincinnati, Ohio. \|\| **924 \| 2019-08-02**: President Trump withdraws
Congressman John Ratcliffe from consideration as Director of National
Intelligence. \| President Trump announces that he has reached a deal
with the European Union that will allow the United States to sell more
beef to Europe. \|\| **925 \| 2019-08-03**: Twenty-three people are
killed and 24 injured at a Walmart Supercenter in El Paso, Texas. The
suspect, Patrick Crusius, is captured by police. \| Speaking from his
golf resort in Bedminster, N.J., President Trump condemns the shooting,
calling it an “act of cowardice”. \|\| **926 \| 2019-08-04**: A mass
shooting occurs in the Oregon District of Dayton, Ohio, at 1:00
a.m.-less than 24 hours after the El Paso shootings-leaving nine dead
and at least 27 injured. The gunman, Connor Stephen Betts, is killed at
the scene attempting to enter the Ned Peppers Bar. \| In New Jersey,
President Trump declares “hate has no place in our country” and suggests
that mental illness played a role in both shootings. \|\| **927 \|
2019-08-05**: President Trump addresses the nation in regards to the
mass shootings in El Paso, Texas, and Dayton, Ohio, offering his
condolences to the victims and their families. \|\| **929 \|
2019-08-07**: President Trump and First Lady Melania Trump visit victims
of Dayton and El Paso mass shootings. \| The Senate confirms Kelly Craft
as the next United States ambassador to the United Nations in a 56-34
vote. \|\| **934 \| 2019-08-12**: The Trump administration announces a
new immigration policy designed to limit the number of green card
applicants from legal migrants. \|\| **935 \| 2019-08-13**: President
Trump visits the Shell Pennsylvania Petrochemicals Complex. \|\| **937
\| 2019-08-15**: President Trump holds a rally in Manchester, New
Hampshire. \| Dan Coats steps down as Director of National Intelligence.
With the resignation of acting director Sue Gordon, Joseph Maguire, the
leader of the National Counterterrorism Center, will become the acting
Director of National Intelligence. \|\| **938 \| 2019-08-16**: President
Trump expresses interest in purchasing Greenland from Denmark. Both
Danish and Greenlandic officials reject the proposal. \|\| **942 \|
2019-08-20**: President Trump holds a bilateral meeting with Romanian
president Klaus Iohannis at the White House. \| President Trump asserts
that any Jew who votes for a Democrat is either, “disloyal or
unintelligent”. \|\| **943 \| 2019-08-21**: President Trump proclaims “I
am the chosen one” to reporters at the White House. \|\| **944 \|
2019-08-22**: President Trump presents the Presidential Medal of Freedom
to NBA legend Bob Cousy. He also jokingly adds he would like to “give
myself a Medal of Honor”. \|\| **945 \| 2019-08-23**: President Trump
asserts that he reserves the right to order U.S. companies to stop doing
business with China. \|\| **946 \| 2019-08-24**: President Trump attends
the 45th G7 summit in Biarritz and holds a bilateral meeting with French
President Emmanuel Macron. \|\| **947 \| 2019-08-25**: President Trump
holds bilateral meetings with Australian prime minister Scott Morrison,
British prime minister Boris Johnson, Canadian prime minister Justin
Trudeau and Japanese prime minister Shinzo Abe. \|\| **948 \|
2019-08-26**: President Trump holds bilateral meetings with Egyptian
president Abdel Fattah el-Sisi, German chancellor Angela Merkel and
Indian prime minister Narendra Modi. \| President Trump fails to attend
the G7 discussion on climate, biodiversity, and the Amazon forest fires.
The White House makes false claims stating Trump was attending other
engagements with German chancellor Angela Merkel and Indian prime
minister Narendra Modi. Both leaders attend the climate session. \|
President Trump holds a joint press conference with French president
Emmanuel Macron. \|\| **950 \| 2019-08-28**: President Trump announces a
new administration rule that citizenship will no longer be automatic for
children of some U.S. military members living overseas. \|\| **951 \|
2019-08-29**: President Trump establishes the U.S. Space Command. \|
Department of Justice (DOJ) Inspector General Michael E. Horowitz
releases a report stating that James Comey violated FBI rules. \| The
Trump administration and the Environmental Protection Agency (EPA)
announce a reduction of restrictions on the production of Methane, a
powerful greenhouse gas. \| Madeleine Westerhout, President Trump’s
personal assistant, resigns after sharing private details about the
president’s family with journalists. \|\| **952 \| 2019-08-30**:
President Trump tweets a high-resolution aerial image of a failed
Iranian missile launch. Ankit Panda, who specializes in analyzing
satellite imagery at the Federation of American Scientists, remarked
“The resolution is amazingly high. I would think it’s probably below
well below 20 centimeters, which is much higher than anything I’ve ever
seen,” adding the image disclosed “some pretty amazing capabilities that
the public simply wasn’t privy to before this.” The image appeared to be
a snapshot of a physical photograph, which a defense official said had
been included in Trump’s intelligence briefing that morning. Satellite
tracking analysts concluded the image was likely taken by the USA-224
reconnaissance satellite. Some intelligence veterans expressed dismay
that Trump tweeted the image, which he asserted he had the “absolute
right to do”. \|\| **953 \| 2019-08-31**: A mass shooting occurs in the
cities of Midland and Odessa, Texas, leaving seven dead and 22 injured.
The perpetrator, Seth Ator, is shot by police and dies at the scene.
\|\| **956 \| 2019-09-03**: Secretary of Defense Mark Esper authorizes
the transfer of 3.6 billion dollars of military funds to the
construction Mexican border wall. \|\| **958 \| 2019-09-05**: President
Trump presents the Presidential Medal of Freedom to Jerry West. \|\|
**959 \| 2019-09-06**: A report shows that the United States added
130,000 jobs in August, missing economists’ expectations; the national
unemployment rate remains unchanged at 3.7%. \|\| **962 \| 2019-09-09**:
President Trump awards the Medal of Valor to the first responders in the
mass shootings in Dayton, Ohio, and El Paso, Texas. \| President Trump
holds a rally in Fayetteville, North Carolina. \|\| **963 \|
2019-09-10**: National Security Advisor John Bolton resigns following
President Trump’s request the day before. \| Charles Kupperman is named
acting national security advisor after John Bolton was asked to resign.
\|\| **964 \| 2019-09-11**: President Trump and First Lady Melania Trump
lay a wreath at the September 11 memorial at the Pentagon and later pay
tribute to all the nearly three thousand Americans killed that day,
pledging to continue to confront radical Islamic terrorism. \| The Trump
administration announces that it will ban the sale of flavored
e-cigarettes, in response to numerous mysterious respiratory diseases
that appear to have been caused by vaping. \|\| **966 \| 2019-09-13**:
Trump administration opens huge reserve in Alaska to drilling. \|\|
**969 \| 2019-09-16**: President Trump presents the Presidential Medal
of Freedom to Mariano Rivera. \| President Trump hosts Crown Prince
Salman of Bahrain at the White House. \| President Trump holds a rally
in Rio Rancho, New Mexico. \|\| **970 \| 2019-09-17**: President Trump
arrives in California for a two-day fundraising visit to benefit the
Trump Victory Committee. \|\| **971 \| 2019-09-18**: President Trump
visits San Diego, California, and meets with Border Patrol personnel. \|
President Trump names Robert O’Brien as the next National Security
Advisor. \| President Trump announces on Twitter that he is revoking
California’s ability to set its own auto emissions standards. \|\| **972
\| 2019-09-19**: President Trump meets with Facebook CEO Mark
Zuckerberg, in an unannounced meeting. This was the first face-to-face
meeting between the two men. \|\| **973 \| 2019-09-20**: Australian
prime minister Scott Morrison, accompanied by his wife, begins a state
visit, his second during the Trump presidency. \| President Trump holds
a bilateral meeting and joint press conference with Australian prime
minister Scott Morrison at the White House. \| President Trump and First
Lady Melania Trump host their second state dinner in honor of Australian
prime minister Scott Morrison and his wife, Jenny. \|\| **975 \|
2019-09-22**: President Trump attends a “Howdy, Modi” rally with Indian
prime minister Narendra Modi in Houston, Texas. \| President Trump
visits Pratt Industries plant with Australian prime minister Scott
Morrison in Wapakoneta, Ohio. \|\| **976 \| 2019-09-23**: President
Trump attends the United Nations event on “Religious Freedom” at the
Headquarters of the United Nations. \| President Trump holds bilateral
meetings with Pakistani president Imran Khan, Polish president Andrzej
Duda, New Zealand prime minister Jacinda Ardern, Singaporean prime
minister Lee Hsien Loong, Egyptian president Abdel Fattah el-Sisi, and
South Korean president Moon Jae-in at the UN General Assembly in New
York City. \| President Trump admits to pressuring the Ukrainian
president Volodymyr Zelensky, during a phone call on July 25, to
investigate potentially damaging information against Democratic
candidate Joe Biden’s son, Hunter. \|\| **977 \| 2019-09-24**: President
Trump addresses the United Nations General Assembly at the Headquarters
of the United Nations. \| President Trump holds bilateral meetings with
British prime minister Boris Johnson and Indian prime minister Narendra
Modi at the UN General Assembly in New York City. \| While at the United
Nations, President Trump tweets that he will release a memorandum of his
July phone call to Ukrainian President Volodymyr Zelensky, in which they
reportedly discussed Joe Biden, Hunter Biden, and the 2020 American
election. \| Speaker of the House Nancy Pelosi announces that the House
of Representatives will launch a formal impeachment inquiry against
President Trump. \|\| **978 \| 2019-09-25**: President Trump holds
bilateral meetings with Japanese prime minister Shinzo Abe, Ukrainian
president Volodymyr Zelensky, and Salvadoran president Nayib Bukele at
the UN General Assembly in New York City. \| A whistleblower complaint
that was filed on August 12 is declassified and released to the public
by a 421-0 vote in the House of Representatives. It accuses President
Trump of “abus\[ing\] his office for personal gain” by “\[soliciting\]
interference” from Ukraine in the 2020 election and that the White House
took steps to cover it up“. Michael Atkinson, the Inspector General for
the Intelligence Community, had deemed the complaint”urgent and
credible" and submitted it to the acting Director of National
Intelligence Joseph Maguire. \| A release of President Trump’s call with
Ukrainian president Volodymyr Zelensky shows that President Trump
repeatedly pressured Zelensky to investigate the potential 2020
presidential candidate and former Vice President Joe Biden and his son
Hunter with Rudy Giuliani and Attorney General William Barr. \|\| **979
\| 2019-09-26**: President Trump visits the United States Mission to the
United Nations. \| Acting Director of National Intelligence Joseph
Maguire meets with the House Intelligence Committee to discuss the
whistleblower complaint and the transcript of the phone conversation
between the two presidents. Maguire supported his decision to delay
informing Congress of the whistleblower document as required but instead
having diverted the complaint to the Justice Department and the White
House for review. \| The Senate confirms Eugene Scalia as the 28th U.S.
secretary of labor in a vote of 53-44. \| The Administration says it
plans to allow only 18,000 refugees to resettle in the United States in
the 2020 fiscal year, its lowest level since the modern program began in
1980. \|\| **980 \| 2019-09-27**: President Trump celebrates Hispanic
Heritage Month at the White House. \| President Trump’s special envoy
for Ukraine Kurt Volker resigns amid reports that he introduced Trump’s
personal attorney, Rudy Giuliani, to Ukrainian officials. \|\| **983 \|
2019-09-30**: Eugene Scalia is sworn in as the 28th U.S. Secretary of
Labor. \| A White House official reports that President Trump pressured
Australian prime minister Scott Morrison to find information for a
Justice department inspection of the Mueller investigation in an attempt
to destroy said investigation. \|\| **984 \| 2019-10-01**: President
Trump accuses the impeachment inquiry against him of being a coup
d’etat, designed to strip Americans of their freedoms. \| Secretary of
State Mike Pompeo calls congressional demands for interviews in front of
committees “an act of intimidation”. \|\| **985 \| 2019-10-02**:
President Trump holds a bilateral meeting and joint press conference
with Finnish president Sauli Niinisto at the White House. While
responding to reporters about the impeachment inquiry, President Trump
calls Adam Schiff a “low life” and the whistle-blower’s source a “spy”.
\| After previously evading questions, Secretary of State Mike Pompeo
admits he was a listener on the July 25 call between President Trump and
Ukrainian president Volodymyr Zelensky. \| President Trump expresses
interest in building an electrified moat filled with alligators along
the southern border with Mexico, forcing his aides to find a cost
estimate. He also proposes shooting migrants in the legs in order to
slow them down and threatens to close the 2,000 mile border with Mexico
in an effort to control immigration. \| White House officials tell
reporters that President Trump frequently engaged Vice President Mike
Pence in the president’s efforts to pressure Ukrainian president
Volodymyr Zelensky to find damning information on Joe Biden and his son,
Hunter. \|\| **986 \| 2019-10-03**: President Trump publicly urges China
and Ukrainian president Volodymyr Zelensky to investigate former Vice
President Joe Biden and his family on national television. \|\| **989 \|
2019-10-06**: A second whistle-blower comes forward to the U.S.
intelligence community with corroborating first-hand information
concerning President Trump’s call with Ukrainian president Volodymyr
Zelensky. \|\| **990 \| 2019-10-07**: President Trump signs the
U.S.-Japan trade agreement. \| President Trump announces a Sunday night
decision to withdraw U.S. special forces from northeastern Syria. \| The
House Intelligence, Foreign Affairs and Oversight committees subpoena
the Department of Defense and the White House Office of Management and
Budget for documents related to Ukraine. \| The Trump administration
announces it is adding 28 Chinese corporations to a blacklist over
concerns of the role the companies played in human rights violations,
barring American companies from doing business with these companies.
\|\| **991 \| 2019-10-08**: President Trump presents the Presidential
Medal of Freedom to former Attorney General Edwin Meese. \| The House
announces that it will subpoena Gordon Sondland to testify and hand over
any documents to the Impeachment inquiry after the State Department
blocked Sondland’s testimony. \| The Trump administration announces in a
letter to Speaker of the House Nancy Pelosi that it will not cooperate
in any way with the impeachment inquiry, calling it “illegitimate” and
“dangerous”, effectively challenging Congress’s constitutional power.
\|\| **993 \| 2019-10-10**: President Trump holds a rally in
Minneapolis, Minnesota. \| Michael McKinley resigns his position as
senior advisor to Secretary of State Mike Pompeo. \|\| **994 \|
2019-10-11**: President Trump holds a rally in Lake Charles, Louisiana.
\| Acting Secretary of Homeland Security Kevin McAleenan, the fourth
person to serve in that post during the Trump presidency, resigns.
“Kevin McAleenan has done an outstanding job.” President Trump tweets
that he will announce a replacement in the coming days. \| Secretary of
State Mike Pompeo defends President Trump’s call with the Ukrainian
president and accuses Democratic members of Congress of “trying to take
down this president”, saying that is commonplace to ask allies to “do
things for us”. \| Former U.S. Ambassador to Ukraine Marie Yovanovitch,
in defiance of a White House ban on cooperating with Congress, tells the
House impeachment inquiry that Trump personally pressured the State
Department to have her ousted from her position. \|\| **997 \|
2019-10-14**: President Trump falsely claims that Kurdish
soldiers-former allies in the War against ISIS-are releasing ISIS POWs
during the Turkish invasion of Syria following President Trump’s order
for U.S. troops to vacate the country. \| President Trump announces
sanctions on Turkey following backlash from Republican Party congressmen
over the president’s withdrawal of American troops stationed in Syria.
\| Fiona Hill, past senior official for Russia and Europe on the
National Security Council, testifies for nine hours before House panels
regarding a July 10 meeting with senior Ukrainian officials,
then-National Security Adviser John Bolton, and other U.S. officials
including U.S. ambassador to the European Union, Gordon Sondland. \|\|
**998 \| 2019-10-15**: President Trump entertains the St. Louis Blues,
2019 Stanley Cup champions, at the White House. \| George Kent, deputy
assistant secretary of state responsible for Ukraine, testifies in the
House impeachment inquiry of President Trump. \|\| **999 \|
2019-10-16**: President Trump holds a bilateral meeting and joint press
conference with Italian president Sergio Mattarella at the White House.
\| The House of Representatives formally condemns President Trump’s
withdrawal of troops from Syria by a vote of 354-60. \| President Trump
holds a White House meeting with key Democrats and Republicans on Syria.
After the meeting, House Speaker Nancy Pelosi and some Democrats contend
that the president was “having a meltdown”, calling the speaker a
“third-rate politician”. \| Special Envoy to Ukraine Kurt Volker and
Michael McKinley, recently resigned senior adviser to Secretary of State
Mike Pompeo, testify in closed-door sessions before the House
impeachment inquiry. \|\| **1000 \| 2019-10-17**: Vice President Mike
Pence and Turkish president Recep Tayyip Erdogan agree to a ceasefire
regarding the Turkish invasion of Kurdish-held northeastern Syria. \|
Acting White House chief of staff Mick Mulvaney confirms Trump blocked
military aid to Ukraine in order to force investigation of his political
rivals. Mulvaney called the quid pro quo exchange “absolutely
appropriate” and “we do that all the time with foreign policy.” \|
Acting White House chief of staff Mick Mulvaney defends President
Trump’s decision to hold the 2020 G-7 summit at the Trump National Doral
Miami Golf Club. \| President Trump holds a rally in Dallas, Texas. \|
Energy Secretary Rick Perry informs President Trump of his plans to
resign. \| Ambassador to the European Union, Gordon Sondland, testifies
before the House impeachment inquiry. \|\| **1002 \| 2019-10-19**: In
response to fierce criticism from Congress, President Trump announces on
Twitter that he will no longer be holding the 2020 G-7 summit at Trump
National Doral Miami, instead considering Camp David as a possible
alternative. \|\| **1004 \| 2019-10-21**: Russ Vought, acting director
of the Office of Management and Budget, refuses to testify in the House
impeachment inquiry. \| During an interview on Fox News with Sean
Hannity, Donald Trump says both The New York Times and The Washington
Post treat him terribly with very negative stories and that he will
cancel White House subscriptions to these newspapers. \|\| **1005 \|
2019-10-22**: Bill Taylor, an American diplomat to Ukraine, testifies to
the House impeachment inquiry that President Trump directed officials to
deny foreign aid to Ukraine if the country would refuse to open an
investigation into Joe Biden and his son. \| Kelly Ann Shaw, a senior
woman on President Trump’s economic team, announces she will be leaving
as deputy assistant to the president for international economic affairs
and deputy director of the National Economic Council. \| White House
press secretary Stephanie Grisham confirms Trump’s statements and says
the White House is cancelling subscriptions to two both The Washington
Post and The New York Times. \|\| **1006 \| 2019-10-23**: President
Trump announces the removal of sanctions against Turkey, resulting from
the negotiation of a ceasefire on Turkey’s invasion of Kurdish-held
Syria. President Trump also says American involvement in Syria is over,
adding that he will “let someone else fight over this long bloodstained
sand”. \| Deputy Assistant Secretary of Defense Laura Cooper, a Pentagon
official in charge of Ukraine policy, testifies to the House Impeachment
inquiry after a five-hour delay. \|\| **1007 \| 2019-10-24**: President
Trump presents the Presidential Medal of Freedom to Roger Penske. \| A
federal judge holds that Education Secretary Betsy DeVos is in contempt
of court for violating an order to stop collecting on student loans.
\|\| **1009 \| 2019-10-26**: Philip T. Reeker, acting assistant
secretary of state, testifies to the House impeachment inquiry that he
was unaware of President Trump’s request for an investigation of the
Bidens by Ukrainian authorities until the whistle-blower report was made
public. \|\| **1010 \| 2019-10-27**: President Trump confirms that ISIS
leader Abu Bakr al-Baghdadi detonated an explosive vest in a
confrontation with American troops in northwest Syria, killing himself
and three of his six children. \|\| **1011 \| 2019-10-28**: Charles
Kupperman, former deputy national security advisor, defies a
congressional subpoena and fails to appear for a deposition before House
impeachment investigators. Kupperman, who listened in to the July 25
telephone call between President Trump and Ukrainian president Zelensky,
sought guidance from a federal judge about whether he should testify. In
an effort to prevent Kupperman from testifying, President Trump invoked
constitutional immunity, thereby preventing Kupperman from testifying to
Congress. \|\| **1012 \| 2019-10-29**: Director of the National Security
Council (NSA) Lieutenant Colonel Alexander S. Vindman testifies to the
House Impeachment inquiry about outside influencers who promoted “a
false and alternative narrative” that was not helpful “to U.S. national
security”. \|\| **1013 \| 2019-10-30**: President Trump presents the
Medal of Honor to Army Master Sergeant Matthew O. Williams. \| Catherine
Croft, a State Department Ukraine expert and National Security Council
(NSC) staff member, testifies to the House Impeachment inquiry.
Christopher J. Anderson, a career Foreign Service officer, testifies
later in the day. \| Timothy Morrison, a top adviser for Russian and
European affairs, announces that he is leaving his job. He is scheduled
to testify before the House impeachment investigators the following day.
\|\| **1014 \| 2019-10-31**: The House of Representatives votes to
formally endorse the impeachment inquiry 232-196, mostly along partisan
lines. White House press secretary Stephanie Grisham condemns the vote,
calling the inquiry a “a blatantly partisan attempt to destroy the
president”. \| Timothy Morrison testifies to the House impeachment
inquiry that he was informed that President Trump wanted Ukrainian
officials to launch an investigation to help him in return for American
aid to the country. \|\| **1015 \| 2019-11-01**: President Trump holds a
rally in Tupelo, Mississippi. \| Chad Wolf, a key architect of the Trump
administration’s “zero tolerance” immigration policy, is appointed as
the latest acting secretary of the Department of Homeland Security. \|\|
**1017 \| 2019-11-03**: President Trump blames Governor Gavin Newsom for
the many wildfires that are currently raging across California and
threatens to withhold funding to fight the fires on Twitter. Trump
tweets that Newsom has “done a terrible job of forest management”,
causing the string of recent fires. Of the 33 million acres of forest in
California, 57% is controlled by the federal government. \|\| **1018 \|
2019-11-04**: President Trump holds a rally in Lexington, Kentucky. \|
National Security Council attorneys John Eisenberg and Michael Ellis,
along with senior advisor to chief of staff Mick Mulvaney and assistant
to the president Robert Blair, and Brian McCormick, an official at the
Office of Management and Budget were scheduled to testify at the
Impeachment inquiry. All four fail to show. \| The House committees
leading the Impeachment inquiry begin releasing transcripts from last
months closed-door testimonies beginning with former Ambassador to
Ukraine Marie Yovanovitch and former State Department official Michael
McKinley. \|\| **1019 \| 2019-11-05**: The House committees release
transcripts from Gordon Sondland, the United States ambassador to the
European Union, and Kurt Volker, the former special envoy to Ukraine.
\|\| **1020 \| 2019-11-06**: President Trump holds a rally in Monroe,
Louisiana. \| The House committees release the transcript from the
former ambassador to Ukraine, Bill Taylor. \|\| **1021 \| 2019-11-07**:
A New York State Judge orders President Trump to pay two million dollars
to various non-profit organizations for his abuse of the Trump
Foundation to advance his 2016 presidential campaign. \| Former national
security advisor John Bolton fails to appear before the House
impeachment inquiry to give a testimony. The inquiry decides not to
issue a subpoena though, as Bolton’s attorney threatened to go to court
if one was issued. \| Jennifer Williams, a national security aide to
Vice-president Mike Pence, testifies in the ongoing House impeachment
inquiry while the White House tries to prevent her from giving a
deposition. George Kent, a State Department official, also testifies.
\|\| **1023 \| 2019-11-09**: President Trump announces that he will
release the transcript of a second phone call with Ukrainian president
Volodymyr Zelensky. \|\| **1025 \| 2019-11-11**: President Trump
participates in the Veterans Day parade in New York City, among other
events. \|\| **1027 \| 2019-11-13**: In the first day of public
broadcast of the Trump Impeachment Hearing, the House Intelligence
Committee hears testimony from William Taylor, the top diplomat in
Ukraine, and George Kent, a senior State Department official. \|
President Trump holds a bilateral meeting and joint press conference
with Turkish president Recep Tayyip Erdogan at the White House. \|\|
**1028 \| 2019-11-14**: President Trump holds a bilateral meeting with
NATO Secretary General Jens Stoltenberg at the White House. \| President
Trump holds a rally in Bossier City, Louisiana. \| A mass shooting
occurs at Saugus High School in Santa Clarita, California, killing two
and injuring three others. The suspect, 16 year-old Nathaniel Berhow is
critically injured and dies the next day. \|\| **1029 \| 2019-11-15**:
Marie Yovanovitch testifies for a second time before the House
Intelligence Committee about her recollections surrounding President
Trump’s July 25 call with Ukrainian president Volodymyr Zelensky.
Yovanovitch claims Rudy Giuliani and others “with questionable motives”
led a “campaign of disinformation”. President Trump attacks Yovanovitch
on Twitter, even as she testifies about feeling threatened by his July
25 comments, which Yovanovitch called “very intimidating”. \| David
Holmes, a career diplomat and the political counselor at the embassy in
Kyiv, testifies before lawmakers in a closed-door meeting as part of the
House Impeachment inquiry. He claimed to have overheard President Trump
talking with a U.S. Ambassador Sondland. \| In an attempt to clear
himself, President Trump releases a rough transcript of the first phone
call between Trump and Ukrainian president Zelensky, which occurred on
April 21. \|\| **1030 \| 2019-11-16**: Mark Sandy, a senior career
official at the Office of Management and Budget (OMB) testifies
privately to the House impeachment inquiry that he did not understand
why American aid to Ukraine had been delayed, adding that he had never
before encountered a similar situation during his time at the OMB. \|
Jennifer Williams, an aide to Vice President Mike Pence, testifies in
closed-door session under subpoena before the House Impeachment inquiry
\| President Trump makes an unscheduled visit to Walter Reed National
Military Medical Center to “begin portions of his routine annual
physical exam” that included a “quick exam and labs”, according to the
White House. \|\| **1033 \| 2019-11-19**: Lieutenant Colonel Alexander
Vindman, Department of State official Jennifer Williams, former U.S.
Ambassador to NATO Kurt Volker and advisor to the president Tim Morrison
all testify publicly before the House impeachment inquiry. Volker
changes his previous testimony after learning that “a great deal of new
information” had been revealed. \|\| **1034 \| 2019-11-20**: President
Trump visits an Apple manufacturing plant in Austin, Texas. \| U.S.
Ambassador to the European Union Gordon Sondland testifies publicly to
the House impeachment inquiry that he worked with Rudy Giuliani to
pressure Ukraine to investigate Joe Biden at the “express direction of
the president”. \| Laura Cooper, a top Pentagon official, and David
Hale, the undersecretary of state for political affairs, testify
publicly to the House impeachment inquiry that Ukrainian officials knew
about delayed American aid as early as July, undermining President
Trump’s defense that there was no “quid pro quo”. \|\| **1035 \|
2019-11-21**: Former advisor to the president Fiona Hill testifies
publicly to the House impeachment inquiry that President Trump’s
pressure on Ukrainian officials to open investigations into his rivals
was a “domestic political errand” which damaged American foreign policy,
refuting the “fictional narrative” presented by President Trump and his
allies. Diplomat David Holmes also testifies publicly to the House
impeachment inquiry about a conversation he overheard between Ambassador
Sondland and President Trump in which the president repeatedly sought
information concerning the investigations into the 2016 presidential
election. \|\| **1038 \| 2019-11-24**: Secretary of the Navy Richard V.
Spencer is fired by Secretary of Defense Mark Esper over a dispute
between President Trump and Spencer after the president intervened in
the war crimes trial of Chief Petty Officer Eddie Gallagher, a Navy SEAL
commando. \|\| **1039 \| 2019-11-25**: President Trump holds a bilateral
meeting with Bulgarian prime minister Boyko Borisov at the White House.
\| A federal judge rules that former White House counsel Don McGahn must
be allowed to testify to the House impeachment inquiry, overruling
President Trump’s assertion of executive privilege over McGahn, adding
that “presidents are not kings.” \|\| **1040 \| 2019-11-26**: President
Trump and First Lady Melania Trump participate in the National
Thanksgiving Turkey Presentation. \| President Trump holds a rally in
Sunrise, Florida. \| Chairman of the House Judiciary Committee Jerrold
Nadler invites President Trump and his legal counsel to participate in
the impeachment inquiry, allowing him to ask questions of witnesses.
\|\| **1042 \| 2019-11-28**: President Trump and First Lady Melania
Trump make an unannounced Thanksgiving visit in order to meet with
American troops stationed in a combat zone at Bagram Airfield in
Afghanistan. \|\| **1045 \| 2019-12-01**: President Trump’s legal team
announces that they will not accept the House Judiciary Committee’s
invitation to participate in the impeachment inquiry over complaints
that the inquiry lacked “any semblance of a fair process”. \| Today is
Secretary of Energy Rick Perry’s official last day, following his
previous letter of resignation to President Trump. \|\| **1046 \|
2019-12-02**: President Trump arrives in London for the upcoming NATO
summit. \| The Senate confirms Dan Brouillette, a former lobbyist for
Ford Motor Company as the next secretary of energy, succeeding Rick
Perry. \|\| **1047 \| 2019-12-03**: President Trump holds bilateral
meetings with NATO secretary general Jens Stoltenberg, French president
Emmanuel Macron and Canadian prime minister Justin Trudeau. \| President
Trump and First Lady Melania Trump attend a NATO dinner hosted by Queen
Elizabeth II at Buckingham Palace. \| In a 300-page report the House
Intelligence Committee accuses President Trump of placing his “personal
and political interests above the national interests of the United
States” and jeopardizing national security through his requesting of
foreign assistance to aid his political campaign. \|\| **1048 \|
2019-12-04**: President Trump holds bilateral meetings with German
chancellor Angela Merkel, Danish prime minister Mette Frederiksen and
Italian prime minister Giuseppe Conte, cancels a scheduled press
conference and leaves the Nato summit early. \| The House impeachment
inquiry invites four legal scholars to testify whether President Trump’s
actions concerning Ukraine warranted impeachment. Three scholars said
the president’s actions did require impeachment, saying that Trump’s
conduct was worse than any preceding president. One scholar did not
agree with the others, adding that impeachment would set a “dangerous
precedent” in future impeachments. \|\| **1049 \| 2019-12-05**: Speaker
of the House Nancy Pelosi announces that the House committee chairmen
will proceed with articles of impeachment against President Trump,
adding that the “President leaves us no choice”. \|\| **1053 \|
2019-12-09**: The House impeachment inquiry hears arguments both for and
against impeachment of President Trump from Republican and Democratic
lawyers, who argue that “the Democrats are obsessed with impeaching
President Trump” and the evidence against the president “is
overwhelming”, respectively. \| The Democratic members of the House of
Representatives announces that it will release articles of impeachment
against President Trump on December 10. \|\| **1054 \| 2019-12-10**:
President Trump meets with Russian foreign minister Sergey Lavrov. \|
President Trump holds a rally in Hershey, Pennsylvania. \| House
Democratic leaders release two articles of impeachment against President
Trump, contempt of Congress and abuse of power. \|\| **1055 \|
2019-12-11**: President Trump signs an executive order defining Judaism
as a nationality or race, not just as a religion, in response to
increased anti-Semitism in universities. \|\| **1057 \| 2019-12-13**:
The House Judiciary committee votes along party lines to approve the two
articles of impeachment against President Trump, sending the articles to
the House floor for further debate and voting. \| President Trump holds
a bilateral meeting with Paraguayan president Mario Abdo Benitez at the
White House. \|\| **1061 \| 2019-12-17**: President Trump holds a
bilateral meeting with Guatemalan president Jimmy Morales at the White
House. \|\| **1062 \| 2019-12-18**: President Trump holds a rally in
Battle Creek, Michigan. \| President Trump is impeached by the House of
Representatives on charges of abuse of power and obstruction of Congress
in a vote of 230-197 on the first article and 229-198 on the second
article of impeachment. \|\| **1063 \| 2019-12-19**: Acting U.S.
Ambassador to Ukraine William Taylor, a key witness in the congressional
impeachment inquiry into President Trump, announces that he will step
down from his post and leave Kiev before Secretary of State Mike Pompeo
visits in early January 2020. \| The United States-Mexico-Canada
Agreement (USMCA), President Trump’s replacement for the North American
Free Trade Agreement (NAFTA), is passed by the House of Representatives
in a vote of 385-41. \| Christianity Today, a conservative evangelical
Christian magazine, publishes an editorial calling for President Trump
to be “removed from office” due to his violation of the Constitution and
“profoundly immoral actions”. \|\| **1064 \| 2019-12-20**: The First
Family depart Washington for an extended Holiday stay at President
Trump’s Mar-a-Lago resort in Palm Beach, Florida. \|\| **1065 \|
2019-12-21**: President Trump complains that windmills are “very
expensive”, claiming that they “kill many bald eagles” and that “he has
studied \[wind power\] better than anybody” during a speech to a group
of young conservative supporters in West Palm Beach, Florida. \|\|
**1071 \| 2019-12-27**: President Trump retweets an article from the
Washington Examiner that contains the name of the alleged whistle-blower
who started his impeachment inquiry. Legal experts disagree on whether a
tweet that reveals the name of a whistle-blower violates the
Intelligence Community Whistleblower Protection Act, as the law forbids
individuals from retaliating against whistle-blowers, but not from
revealing their names. \| The Federal Reserve releases a study showing
that President Trump’s tariffs have led to both job losses and higher
consumer prices. \| The K-1 Air Base in Iraq, which hosts Iraqi and U.S.
military personnel, is attacked, killing an American contractor. \|\|
**1073 \| 2019-12-29**: The U.S. Department of Defense reports a series
of airstrikes against Kata’ib Hezbollah’s weapons depots and command
centers in Iraq and Syria, reportedly killing at least 25 militiamen and
wounding 55 more. \|\| **1075 \| 2019-12-31**: The American embassy in
Iraq is attacked by protestors angered by U.S. air strikes targeting the
Iran-backed militia group, Kataib Hezbollah. \| President Trump calls
the impeachment proceedings against him in Congress a “big fat hoax” and
says the Senate trial would go “very quick”. \|\| **1077 \|
2020-01-02**: Major General Qasem Soleimani, Iran’s top security and
intelligence commander, is killed in an airstrike at Baghdad
International Airport. The Department of Defense issues a statement that
the strike had been carried out “at the direction of the President”.
\|\| **1078 \| 2020-01-03**: President Trump announced the death of
Iranian Major General Qasem Soleimani at Mar-a-Lago in Palm Beach,
Florida in his address to the nation stating “at my direction, the
United States military successfully executed a flawless precision strike
that killed the number-one terrorist anywhere in the world, Qasem
Soleimani. Soleimani was plotting imminent and sinister attacks on
American diplomats and military personnel, but we caught him in the act
and terminated him”. \|\| **1079 \| 2020-01-04**: President Trump
threatens on Twitter to attack Iranian cultural sites if Iran retaliates
for the assassination of General Soleimani. \|\| **1080 \| 2020-01-05**:
President Trump returns to Washington, DC after spending the holidays at
his Mar-a-Lago estate in Palm Beach, Florida. \|\| **1081 \|
2020-01-06**: The Senate returns from winter break. \| President Trump
holds a bilateral meeting with Saudi Arabian vice minister of defense
Prince Khalid bin Salman. \| Former national security adviser John
Bolton announces that he is willing to testify in the Senate trial of
President Trump if subpoenaed. \|\| **1082 \| 2020-01-07**: The House
returns from winter break. \| President Trump holds a bilateral meeting
with Greek prime minister Kyriakos Mitsotakis at the White House. \| The
Pentagon verifies an attack on U.S. forces: “At approximately 5:30 p.m.
(EST) on January 7, Iran launched more than a dozen ballistic missiles
against U.S. military and coalition forces in Iraq.” \|\| **1083 \|
2020-01-08**: President Trump discusses diplomatic tensions with Iran in
a televised address, warning Tehran of retaliation should they strike
again, adding that “Iran appears to be standing down.” \| Ukrainian
Airlines Flight 752 crashes on departure from Tehran International
Airport, killing all 176 passengers aboard. \| President Trump wishes
North Korean leader Kim Jong-Un happy birthday, calling him a “very good
friend”. \|\| **1084 \| 2020-01-09**: Trump Administration officials,
led by the Secretary of State Pompeo, C.I.A. Director Haspel and Defense
Secretary Esper, hold closed-door classified briefings with the House
and the Senate on the strike that killed Soleimani. \| The House votes
to limit the president’s ability to order military operations against
Iran, unless explicitly authorized by Congress. \| President Trump
suggests that the reason for the Soleimani strike was to prevent a plot
to “blow up the embassy” in Baghdad. \| President Trump holds a rally in
Toledo, Ohio. \| Senate Majority Leader Mitch McConnell endorses a
resolution to change Senate rules to allow it to dismiss the articles of
impeachment against President Trump if they are not transmitted from the
House to the Senate within a period of 25 days. \|\| **1085 \|
2020-01-10**: In an interview with Fox News’s Laura Ingraham, President
Trump says Iran had been targeting four American embassies before he
ordered the killing of Soleimani. “I can reveal that I believe it
would’ve been four embassies.” \|\| **1086 \| 2020-01-11**: Iranian
officials admit that the crash of Ukrainian Airlines Flight 752 was
caused by a missile strike brought about by human error and increased
tensions as a result of “U.S. adventurism”. \|\| **1089 \| 2020-01-14**:
Speaker of the House Nancy Pelosi announces that the House will vote on
Wednesday to send the articles of impeachment against President Trump to
the Senate and appoint impeachment managers. \| President Trump holds a
rally in Milwaukee, Wisconsin. \|\| **1090 \| 2020-01-15**: President
Trump and Chinese vice premier Liu He sign phase one of a trade deal,
pausing two years of dispute between China and the United States. \| The
House votes 228-193 to transmit the articles of impeachment against
President Trump to the Senate and appoints impeachment managers. \|\|
**1091 \| 2020-01-16**: The Senate trial on the removal from office of
President Trump begins. \| The United States-Mexico-Canada Agreement
(USMCA), President Trump’s replacement for the North American Free Trade
Agreement (NAFTA), is ratified by the Senate 89-10. \|\| **1092 \|
2020-01-17**: President Trump entertains the Louisiana State University
football team, 2019 College Football Champions, at the White House. \|\|
**1094 \| 2020-01-19**: President Trump travels to Austin to address the
American Farm Bureau, touting the greatness of his administration
through achievements such as the trade agreement with China and USMCA.
\|\| **1095 \| 2020-01-20**: The fourth year of the Trump presidency
begins. \| President Trump and Vice President Pence visit the Martin
Luther King Jr. Memorial. \| President Trump’s legal team submits a
110-page brief to the Senate concerning the articles of impeachment
against him, arguing that adopting those articles was a “dangerous
perversion of the Constitution” and that President Trump must be
acquitted. \|\| **1096 \| 2020-01-21**: President Trump arrives in
Switzerland to attend the 2020 Davos World Economic Forum. \| President
Trump’s impeachment trial begins as senators debate procedural rules
that will govern the proceedings. Eleven Democratic amendments are
rejected 53-47. \|\| **1097 \| 2020-01-22**: President Trump returns to
the White House from Switzerland. \| The Senate votes 53-47 to approve
the rules of President Trump’s impeachment trial, blocking the inclusion
of new evidence or witness testimony. \| Opening arguments begin, with
impeachment managers accusing Trump of trying to cheat in the upcoming
2020 election, adding that his actions demonstrate that “he believes
that he’s above the law and scornful of constraint.” \|\| **1098 \|
2020-01-23**: Impeachment managers present their case that President
Trump abused his office in an attempt to discredit former vice president
Joe Biden, calling on Republican senators to allow new witness
testimony. \|\| **1099 \| 2020-01-24**: President Trump delivers remarks
at an anti-abortion March for Life rally in Washington, DC. \|
Democratic house managers conclude their opening arguments on the first
article of impeachment, abuse of power, as well as the second article of
impeachment, obstruction of Congress. \|\| **1100 \| 2020-01-25**:
President Trump’s legal defense in his impeachment trial begin opening
arguments, refuting the accusations made by the impeachment managers and
accusing them of trying to remove him from office as they believed they
could not win the 2020 presidential election. \|\| **1102 \|
2020-01-27**: President Trump’s legal defense team continue their
opening statements arguing that Trump did nothing wrong and the
impeachment inquiry was illegitimate from the start. John Bolton makes a
claim that he heard Trump say that he (Trump) wanted the freeze on
military aid to Ukraine to continue until Ukrainian officials announced
investigations into Joe Biden.Alan Dershowitz, a member of President
Trump’s legal counsel, claims that “nothing in the Bolton revelations,
even if true, would rise to the level of an abuse of power, or an
impeachable offense.” \| President Trump holds a bilateral meeting with
Israeli prime minister Benjamin Netanyahu at the White House. \|\|
**1103 \| 2020-01-28**: President Trump holds a joint press conference
with Israeli prime minister Benjamin Netanyahu at the White House to
announce a proposed Middle East peace plan. \| President Trump’s legal
defense team completes its opening arguments. \| President Trump holds a
rally in Wildwood, New Jersey. \|\| **1104 \| 2020-01-29**: President
Trump signs the United States-Mexico-Canada Agreement (USMCA). \| U.S.
senators begin the two-day question portion in President Trump’s
impeachment trial. Senate Republicans move to further block new
witnesses, instead opting to push the trial to a verdict. \|\| **1105 \|
2020-01-30**: U.S. senators conclude the two-day question period in
President Trump’s impeachment trial. \| President Trump holds a rally in
Des Moines, Iowa. \|\| **1106 \| 2020-01-31**: President Trump signs an
executive order adding six more countries to his ban on travel from
certain mainly-Muslim countries. The added countries are Nigeria,
Myanmar, Eritrea, Kyrgyzstan, Sudan, and Tanzania. \| The Senate
formally blocks an attempt to call new witnesses in President Trump’s
impeachment trial in a vote of 51-49, with Senators Mitt Romney and
Susan Collins siding with the Democrats. \|\| **1108 \| 2020-02-02**:
The Trump administration announces travel restrictions on air traffic to
and from China take effect. Secretary of Health and Human Services Alex
Azar declares that COVID-19 “poses a public health emergency in the
United States”. \|\| **1109 \| 2020-02-03**: President Trump’s legal
team and house managers begin closing arguments. \| Senator Lisa
Murkowski (R-AK) calls President Trump’s actions “shameful and wrong”
while announcing that she would vote to acquit him. “I cannot vote to
convict,” Murkowski told the Senate chamber. “The Constitution provides
for impeachment but does not demand it in all instances.” \| President
Trump wins the Republican Iowa Caucus. \|\| **1110 \| 2020-02-04**:
President Trump delivers his third official State of the Union Address.
\| President Trump awards Rush Limbaugh the Presidential Medal of
Freedom during the State of the Union address. \| Senator Susan Collins
(R-ME) announces that she will vote to acquit President Trump in his
impeachment trial, despite saying that what he did was wrong. Collins
says her decision is based on the fact that she believes Trump has
learned from this case" and “will be more careful in the future”. \|\|
**1111 \| 2020-02-05**: President Trump holds a bilateral meeting with
Venezuelan opposition leader Juan Guaido at the White House. \|
President Trump is acquitted by the United States Senate on charges of
abuse of power and obstruction of Congress, 48-52 on the first article
and 47-53 on the second. \| Senator Mitt Romney (R-UT) votes to convict
in President Trump’s impeachment trial on Article I, becoming the only
Republican to do so and the first senator from the same party as the
president to vote for removal from office. \|\| **1112 \| 2020-02-06**:
President Trump speaks about politics at the National Prayer Breakfast.
\| In what he calls a “celebration” President Trump delivers remarks in
the White House East Room to supporters following his acquittal in the
impeachment trial. \| President Trump holds a bilateral meeting with
Kenyan president Uhuru Kenyatta at the White House. \|\| **1113 \|
2020-02-07**: President Trump fires Lieutenant Colonel Alexander Vindman
and ambassador Gordon Sondland in retaliation for their cooperation in
his impeachment inquiry. Vindman’s brother is also fired and escorted
from the White House. \|\| **1115 \| 2020-02-09**: President Trump
attends the National Governors Association dinner. \|\| **1116 \|
2020-02-10**: President Trump holds a rally in Manchester, New
Hampshire. \|\| **1117 \| 2020-02-11**: President Trump wins the 2020
New Hampshire Republican Primary, with the most votes for any incumbent
President in history. \| The Justice Department announces that it will
overrule federal prosecutors in the trial of Trump associate Roger Stone
and seek a shorter sentence than what the prosecutors had recommended.
This comes after President Trump had complained on Twitter that the
sentence the prosecutors had been recommending to Stone was “unfair” and
a “miscarriage of justice”. \| In response to the DoJ request for a
reduced sentence, all four prosecutors (Michael Marando, Adam Jed,
Jonathan Kravis and Aaron Zelinsky) withdraw from the Stone trial. \|\|
**1118 \| 2020-02-12**: President Trump holds a bilateral meeting with
Ecuadorian president Lenin Moreno at the White House. \| Jessie Liu, the
U.S. attorney who headed the prosecutions of Roger Stone and Michael
Flynn, resigns after President Trump’s withdrawal of her nomination as
the Treasury Department’s undersecretary for terrorism and financial
crimes. \|\| **1119 \| 2020-02-13**: President Trump publicly
acknowledges sending Rudy Giuliani to Ukraine in an attempt to find
damaging information on Joe and Hunter Biden, despite his fervent
denials of such a search during his impeachment inquiry and trial. \|\|
**1120 \| 2020-02-14**: Army Secretary Ryan McCarthy announces that the
Army will not investigate or take any disciplinary action against
Lieutenant Colonel Alexander Vindman in spite of President Trump’s
comment that the military should “take a look at” whether Vindman said
“horrible things” about him. \| Justice Department attorney J.P. Cooney
says, “The Government has decided not to pursue criminal charges against
… Andrew G. McCabe …”, ending the nearly two-year-long investigation.
\|\| **1122 \| 2020-02-16**: More than 2,000 former Justice Department
officials present an open letter strongly condemning President Trump and
Attorney General William Barr’s “interference in the fair administration
of justice”, and call on Barr to resign due to his involvement in the
Stone case. \|\| **1124 \| 2020-02-18**: President Trump commutes the
sentences of eleven individuals, including former Illinois governor Rod
Blagojevich, who was convicted of attempting to sell a seat in the U.S.
Senate, former NYPD commissioner Bernie Kerik, financier Mike Milken,
and Eddie DeBartolo Jr., all of whom were convicted on corruption
charges. \|\| **1125 \| 2020-02-19**: President Trump holds a rally in
Phoenix, Arizona. \|\| **1126 \| 2020-02-20**: President Trump fires
acting director of national intelligence, Joseph Maguire, after last
weeks briefing to the House Intelligence Committee by the top election
security official, Shelby Pierson, on Russian interference in the
upcoming 2020 election. The president announced that he was replacing
Maguire with Richard Grenell, the current ambassador to Germany, who
will oversee 17 U.S. intelligence agencies. \| President Trump holds a
rally in Colorado Springs, Colorado. \| Roger Stone is sentenced to 40
months in prison for, in the words of Judge Amy Berman Jackson,
“covering up for the president”. \|\| **1127 \| 2020-02-21**: President
Trump holds a rally in Las Vegas, Nevada. \|\| **1130 \| 2020-02-24**:
President Trump begins a two-day state visit to India. \| President
Trump attends a “Namaste, Trump” rally in Gujarat and visits the Taj
Mahal. \|\| **1131 \| 2020-02-25**: President Trump holds a bilateral
meeting and joint press conference with Indian prime minister Narendra
Modi. \| President Trump attends a state dinner hosted by Indian
president Ram Nath Kovind. \| Supreme Court Justices Sonia Sotomayor and
Ruth Bader Ginsburg are attacked on Twitter by President Trump as he
demands that they recuse themselves from “all Trump, or Trump-related”
cases. \| In a press briefing at the White House, Nancy Messonnier,
Director of National Center for Immunization and Respiratory Diseases
warned of the impending community spread of the coronavirus in the
United States, stating: “Disruption to everyday life might be severe.”
\|\| **1132 \| 2020-02-26**: President Trump and First Lady Melania
Trump return to Washington after a two-day trip to India. \| At the
onset of the COVID-19 pandemic, President Trump announces vice-president
Mike Pence to be in charge of the U.S. coronavirus response. \|\| **1134
\| 2020-02-28**: President Trump holds a rally in North Charleston,
South Carolina. \| President Trump tweets that he will nominate
Representative John Ratcliffe (R-TX) to be his director of national
intelligence. \| National Economic Council Director Larry Kudlow
responds from the White House to questions about the coronavirus. \|\|
**1135 \| 2020-02-29**: President Trump gives a speech in Oxon Hill,
Maryland, to the 2020 Conservative Political Action Conference. \| The
first patient death in the United States from COVID-19 is reported by
Washington state health officials. \|\| **1137 \| 2020-03-02**:
President Trump holds a bilateral meeting with Colombian president Ivan
Duque Marquez at the White House. \| President Trump holds a rally in
Charlotte, North Carolina. \| President Trump meets with representatives
from numerous pharmaceutical companies in an effort to develop an
efficient plan to develop a vaccine and treatments for COVID-19. \|\|
**1138 \| 2020-03-03**: President Trump speaks to the press concerning
the COVID-19 pandemic in the United States after Trump was criticized
for his delayed response to the virus. Trump also disputed the World
Health Organization’s (WHO) official mortality rate for the virus of
3.4%, instead claiming the death rate to be “a fraction of 1%”. \|\|
**1139 \| 2020-03-04**: The total number of deaths in the United States
from the coronavirus disease is eleven, ten in Washington state and one
in California. \|\| **1141 \| 2020-03-06**: President Trump signs the
Coronavirus Preparedness and Response Supplemental Appropriations Act
into law. \| While visiting the CDC center in Atlanta, Georgia,
President Trump praises the CDC’s response to the coronavirus. Trump
also calls Washington state governor Jay Inslee “a snake” for
criticizing his response to the COVID-19 pandemic after Inslee called on
Trump to “\[stick\] to the science and \[tell\] the truth”. \| President
Trump fires acting Chief of Staff Mick Mulvaney and announces
Representative Mark Meadows (R-NC) as his replacement. \|\| **1142 \|
2020-03-07**: President Trump holds a working dinner with Brazilian
president Jair Bolsonaro at Mar-a-Lago. \|\| **1145 \| 2020-03-10**:
President Trump presents the Medal of Freedom to General Jack Keane.
\|\| **1146 \| 2020-03-11**: The total number of deaths in the United
States from the coronavirus disease is 31. Twenty-four are in Washington
state, two are in California, two are in Florida and one is in New
Jersey. There are 1,004 total cases in the United States. \| President
Trump addresses the nation on prime-time television concerning the
COVID-19 pandemic as the total number of confirmed cases passes a
thousand. During the address, Trump announces that he will suspend all
travel to and from Europe for thirty days, starting midnight Friday. The
United Kingdom is exempt from this restriction. \|\| **1147 \|
2020-03-12**: President Trump holds a bilateral meeting with Taoiseach
Leo Varadkar of Ireland at the White House. \| Due to the COVID-19
pandemic, the Dow Jones Industrial Average (DJIA) drops ten percent-its
worst day since 1987. \|\| **1148 \| 2020-03-13**: President Trump
declares a national emergency to mitigate the COVID-19 pandemic. The
declaration opens access to 50 billion in emergency funding, lifts
restrictions on doctors and hospitals, and waives student loan interest.
When challenged about the slow response to provide testing, Trump blamed
prior administrations saying, “I don’t take responsibility at all.” \|\|
**1150 \| 2020-03-15**: Due to the COVID-19 pandemic, the Federal
Reserve cuts interest rates to zero and releases 700 billion in
quantitative easing. \|\| **1151 \| 2020-03-16**: In a press conference
at the White House, President Trump urges Americans to avoid gatherings
of more than ten people, warning that the COVID-19 pandemic could last
into the summer. \| The Dow Jones Industrial Average (DJIA) falls 2,997
points, losing 12.9% in its largest point drop ever. \|\| **1153 \|
2020-03-18**: The number of deaths in the United States from the
coronavirus disease is 150. 68 deaths are in Washington state, 20 in New
York state, 16 in California, 8 in Florida, 7 in Louisiana and 5 in New
Jersey. 15 other states have recorded deaths which combined are 26.
There are 5,726 total cases in the United States. \| President Trump
signs the Families First Coronavirus Response Act, a bill providing sick
leave, unemployment benefits, free coronavirus testing, and food and
medical aid to people affected by the COVID-19 pandemic, into law. \| In
an effort to mitigate the COVID-19 pandemic, President Trump and
Canadian prime minister Justin Trudeau close the border between the
United States and Canada, allowing only essential traffic through. \|\|
**1156 \| 2020-03-21**: President Trump announces in a press conference
that he will invoke the Defense Production Act to increase production of
hospital masks, saying he views the country as entering a wartime
setting and that he is “a wartime president”. \|\| **1159 \|
2020-03-24**: In a virtual town hall held at the White House, President
Trump declares that his hope is that the American economy will open back
up by Easter Sunday, eliciting concerns from the medical and scientific
community. He also expressed desire to ease social distancing
restrictions set up to control the spread of coronavirus. \|\| **1160 \|
2020-03-25**: The number of deaths in the United States from the
coronavirus disease is 826. Two hundred eighty-six are in New York
state, one hundred twenty-six in Washington state, fifty-eight in
California, forty-six in Louisiana and thirty-eight in Georgia.
Thirty-six other states have recorded deaths which combined are two
hundred seventy-four. There are 53,852 total cases in the United States.
\| The Senate passes the 2 trillion Coronavirus Aid, Relief, and
Economic Security Act (H.R. 748), also known as the CARES Act, in a vote
of 96-0. \|\| **1162 \| 2020-03-27**: The House passes the 2 trillion
Coronavirus Aid, Relief, and Economic Security Act (CARES Act), with
President Trump signing the Act into law later that same day. \| In a
press conference on the COVID-19 pandemic, President Trump announces
that the government will buy more than 100,000 ventilators to meet
growing demand. Officials are doubtful whether they can be produced in
time to help hospitals that are currently overwhelmed with patients.
\|\| **1163 \| 2020-03-28**: President Trump visits Naval Air Station
Norfolk to watch the Navy hospital ship Comfort depart for New York
City. \|\| **1167 \| 2020-04-01**: President Trump reveals that his
decision to extend the social distancing guidelines to April 30 was
motivated by models which predicted that if the restrictions were
removed as many as 2.2 million people would die and about half the
country would be infected. President Trump also warned that between
100,000 and 240,000 Americans could become infected in the coming days,
despite strict isolation and distancing guidelines. \| More than 3,600
people have died in the United States from the coronavirus disease.
1,941 have died in New York state, 267 in New Jersey, 259 in Michigan,
239 in Louisiana, 225 in Washington state, 184 in California and 139 in
Georgia. Every other state except Wyoming has recorded at least one
death attributed to the virus. \|\| **1168 \| 2020-04-02**: Acting
Secretary of the Navy Thomas Modly announces he has relieved Captain
Brett Crozier from the USS Theodore Roosevelt (CVN-71) for going outside
the chain of command for help with 114 positive coronavirus cases on
board the aircraft carrier. \| In the daily coronavirus press
conference, Jared Kushner declares that the “notion of the federal
stockpile was it’s supposed to be our stockpile; it’s not supposed to be
state stockpiles that they then use.” \|\| **1169 \| 2020-04-03**:
President Trump notifies Congress he has “removed from office”
Intelligence Community Inspector General Michael Atkinson, the
individual who had informed Congress about the whistleblower complaint
that led to the Ukraine probe and the president’s impeachment. \|\|
**1172 \| 2020-04-06**: President Trump nominates Brian D. Miller to
fill the newly created position of Special Inspector General for
Pandemic Recovery. \|\| **1173 \| 2020-04-07**: President Trump
announces that Kayleigh McEnany will become the 31st White House press
secretary, replacing Stephanie Grisham, who was moved to be the First
Lady’s chief of staff. \| President Trump dismisses Glenn A. Fine as
acting inspector general for the Defense Department, making him
ineligible to chair the recently created Pandemic Response
Accountability Committee that he had been appointed to eight days
previously. \| Acting Navy Secretary Thomas Modly submits a letter of
resignation to Defense Secretary Mark Esper. \|\| **1174 \|
2020-04-08**: The number of deaths in the United States attributed to
the coronavirus disease is 12,956. There are more than 397,000 certified
coronavirus cases. \|\| **1181 \| 2020-04-15**: The number of deaths in
the United States attributed to the coronavirus disease is 25,922. There
are more than 606,800 certified coronavirus cases. \| President Trump
announces that the US will stop funding the World Health Organization
(WHO), after Trump criticized the WHO for being too lenient on China. \|
President Trump threatens to prorogue both houses of Congress in order
to make recess appointments. \|\| **1182 \| 2020-04-16**: President
Trump announces that the states can begin lifting restrictions for
coronavirus by May 1 while acknowledging that the decision to reopen is
best left to the states. \|\| **1183 \| 2020-04-17**: President Trump
openly encourages far-right political groups to protest social
distancing restrictions and calls on states to lift restrictions. \|\|
**1186 \| 2020-04-20**: President Trump announces on Twitter that he
will temporarily suspend all immigration in an effort to protect America
from “the Invisible Enemy”. \|\| **1188 \| 2020-04-22**: The number of
deaths in the United States attributed to the coronavirus disease is
42,200. There are more than 830,000 certified coronavirus cases. \|
Health Dept. official Dr. Rick Bright is fired by President Trump after
questioning the effectiveness of Hydroxychloroquine as a drug to treat
COVID-19 and requesting extensive tests to confirm Trump’s claims. \|\|
**1189 \| 2020-04-23**: After the Senate passes a 480 billion aid bill
to help small businesses and hospitals as well as to increase the number
of COVID-19 tests performed the House of Representatives approves the
bill in a vote of 388-5, sending the bill to President Trump for
signing. \|\| **1190 \| 2020-04-24**: President Trump signs the Paycheck
Protection Program and Health Care Enhancement Act to provide hospitals
with 484 billion in funding to increase COVID-19 testing. \| At the
daily coronavirus press briefing, President Trump promotes the use of
ultraviolet light as a remedy to COVID-19, and muses about injecting
bleach or disinfectant into the lungs or other areas of the body to kill
the virus. \|\| **1194 \| 2020-04-28**: President Trump meets with
Governor of Florida Ron DeSantis in the Oval Office. \|\| **1195 \|
2020-04-29**: President Trump meets with Governor of Louisiana John Bel
Edwards in the Oval Office. \| The number of deaths in the United States
attributed to the coronavirus disease is 53,034. There are more than 1
million certified coronavirus cases. \|\| **1196 \| 2020-04-30**:
President Trump meets with Governor of New Jersey Phil Murphy in the
Oval Office. \|\| **1197 \| 2020-05-01**: President Trump dismisses
Acting Health and Human Services inspector general Christi Grimm, who
had issued an April report describing severe shortages of coronavirus
testing materials and personal protective equipment. \|\| **1199 \|
2020-05-03**: During a Fox News town hall in the Lincoln Memorial,
President Trump revises his forecast for the death toll from COVID-19,
increasing it to 100,000. He also admits the disease has been more
lethal than he expected, adding that early intelligence briefings
indicated the virus was “not a big deal”. \|\| **1201 \| 2020-05-05**:
President Trump tours Honeywell Aerospace. \|\| **1202 \| 2020-05-06**:
President Trump meets with Governor of Iowa Kim Reynolds in the Oval
Office. \| The number of deaths in the United States attributed to the
coronavirus disease is 71,077. There are more than 1.2 million certified
coronavirus cases. \|\| **1203 \| 2020-05-07**: One of Trump’s personal
valets tests positive for coronavirus. White House staffers, including
valets, generally do not wear masks. Trump claims, however, that he
requires all his aides to take rapid tests for the virus before he
travels anywhere with them. \| President Trump meets with Governor of
Texas Greg Abbott in the Oval Office. \| President Trump speaks at the
National Day of Prayer service in the Rose Garden. \| The Justice
Department announces that it is dropping all charges against President
Trump’s former National Security Advisor, Michael Flynn. \|\| **1204 \|
2020-05-08**: President Trump and First Lady Melania Trump participate
in the 75th anniversary of VE Day celebrations. \| Katie Miller, the top
spokesperson for Vice President Mike Pence, tests positive for
coronavirus. She is married to Stephen Miller, a top aide and
speechwriter for President Trump. This suggests multiple people who work
in the West Wing may have been exposed. \|\| **1206 \| 2020-05-10**:
Despite the coronavirus diagnosis for one of his staff members, Vice
President Pence said he would not self-isolate and would continue to
work in person at the White House. Other members of the coronavirus Task
Force, including Drs. Redfield, Hahn, and Fauci, however, planned to
self-isolate. \|\| **1207 \| 2020-05-11**: During a press conference,
CBS News White House correspondent Weijia Jiang asks President Trump,
“Why is this a global competition to you if every day Americans are
still losing their lives?” referring to the number of coronavirus tests
performed daily. Trump responds by saying, “They’re losing their lives
everywhere in the world. And maybe that’s a question you should ask
China. Don’t ask me, ask China that question, OK?”. \|\| **1209 \|
2020-05-13**: President Trump meets with Governor of Colorado Jared
Polis and Governor of North Dakota Doug Burgum. \| The number of deaths
in the United States attributed to the coronavirus disease is 82,350.
There are more than 1.37 million certified coronavirus cases. \|\|
**1210 \| 2020-05-14**: President Trump tours Owens + Minor. \|\| **1212
\| 2020-05-16**: President Trump fires Inspector General of the
Department of State Steve Linick, following reports that Linick was
investigating Secretary of State Mike Pompeo over reports of abuse of
office. \|\| **1214 \| 2020-05-18**: President Trump reveals that he is
taking Hydroxychloroquine, an anti-malarial drug untested for its
effectiveness against COVID-19, despite FDA warnings that it may cause
serious heart problems. \|\| **1216 \| 2020-05-20**: President Trump
meets with Governor of Arkansas Asa Hutchinson and Governor of Kansas
Laura Kelly at the White House. \| The number of deaths in the United
States attributed to the coronavirus disease is 91,937. There are more
than 1.54 million certified coronavirus cases. \|\| **1217 \|
2020-05-21**: President Trump tours Ford Rawsonville Components Plant.
\|\| **1221 \| 2020-05-25**: President Trump performs a wreath-laying
ceremony at the Tomb of the Unknown Soldier at the Arlington National
Cemetery and gives a speech honoring those who have died fighting for
the U.S. \|\| **1222 \| 2020-05-26**: Glenn Fine, the Defense Department
Principal Deputy Inspector General, submitted his resignation, effective
June 1. Fine provided leadership of the coronavirus accountability
review of emergency funds. \|\| **1223 \| 2020-05-27**: President Trump
threatens to close or impose regulation on social media after Twitter
flags his post on mail-in ballots as inaccurate. \| The number of deaths
in the United States attributed to the coronavirus disease is 98,937.
There are more than 1.6 million certified coronavirus cases. \|
President Trump and First Lady Melania Trump attend the attempted launch
of the SpaceX Dragon 2 spacecraft from the Kennedy Space Center.
However, the launch was postponed to May 30 due to the weather. \|\|
**1224 \| 2020-05-28**: President Trump signs an executive order
limiting the legal protection that social media companies have, allowing
federal agencies and regulators to hold them liable if found to be
violating free speech protections by deleting posts or user accounts.
\|\| **1225 \| 2020-05-29**: President Trump warns on Twitter that the
“THUGS” using the protests of the murder of George Floyd, to loot and
destroy businesses in Minneapolis would be shot if looting continued,
adding that “when the looting starts, the shooting starts.” \|\| **1226
\| 2020-05-30**: President Trump attends the second attempted launch of
the SpaceX Dragon 2 spacecraft from the Kennedy Space Center, which the
launch was finally success. \|\| **1227 \| 2020-05-31**: In an early
morning tweet President Trump declares the United States of America will
be designating ANTIFA as a terrorist organization. \| News reports
surface claiming that on Friday night Secret Service agents rushed
President Trump to a White House bunker as hundreds of protesters
gathered outside the executive mansion, some of them throwing rocks and
tugging at police barricades. \|\| **1228 \| 2020-06-01**: In a
conference call with the nation’s governors, President Trump declares
that Chairman of the Joint Chiefs of Staff Mark A. Milley, the nation’s
highest-ranking military officer, was “in charge” of the response to
protests. The nature of Milley’s position was not specified, nor the
legal authority under which he would assume such a position. \|
President Trump delivers a speech in the Rose Garden declaring that he
was “dispatching thousands and thousands of heavily armed soldiers,
military personnel and law enforcement officers to stop the rioting,
looting, vandalism, assaults and the wanton destruction of property,”
and, “If a city or state refuses to take the actions that are necessary
… then I’ll deploy the United States military and quickly solve the
problem for them.” \| After the press conference at the Rose Garden,
Trump walks to the nearby St. John’s Church, where an adjacent building
had experienced a fire the previous night, in Lafayette Square for a
photo op. In preparation for Trump’s arrival, riot police and military
police use tear gas and stun grenades to clear peaceful protesters
assembled at the park. and the clergy at the church. \| The White House
provided clarification for President Trump’s May 31, 2020, announcement
on Twitter that he vows to designate ANTIFA as a terrorist group. \|\|
**1229 \| 2020-06-02**: President Trump and First Lady Melania Trump
visit the Saint John Paul II National Shrine. \|\| **1230 \|
2020-06-03**: President Trump announces that the Republican National
Committee would move the 2020 Republican National Convention from
Charlotte, NC to another location, after North Carolina Governor Roy
Cooper did not find the health and safety measures put forth by the
Republican National Committee to be adequate. \| The number of deaths in
the United States attributed to the coronavirus disease is 106,184.
There are more than 1.8 million certified coronavirus cases. \|\| **1236
\| 2020-06-09**: President Trump asserts on Twitter that Martin Gugino,
elderly man pushed to the ground by police in Buffalo, New York, during
a protest over the killing of George Floyd could be a “set up” that
Gugino was an “ANTIFA provocateur”. \|\| **1237 \| 2020-06-10**: The
number of deaths in the United States attributed to the coronavirus
disease is 112,174. There are more than 1.9 million certified
coronavirus cases. \|\| **1238 \| 2020-06-11**: The Republican National
Committee selects Jacksonville, Florida to host its Aug 27 convention.
\|\| **1240 \| 2020-06-13**: President Trump speaks to the cadets at the
United States Military Academy at West Point graduation ceremony. \|
President Trump announced that the Tulsa, Oklahoma Rally would be held
on July 20, out of respect. \|\| **1242 \| 2020-06-15**: The Supreme
Court rules in a 5-4 decision that LGBT rights are protected against
discrimination by the Civil Rights Act of 1964. \|\| **1243 \|
2020-06-16**: The Trump administration announces that it is ordering
former National Security Advisor John Bolton to cease publication of his
new book, claiming that it violates non-disclosure agreements and
releases classified information. \| Elaine McCusker, CFO of the Defense
Department, resigns. \|\| **1244 \| 2020-06-17**: Solicitor General Noel
Francisco, who defended Trump administration policies before the Supreme
Court, announces he is leaving the Department of Justice. \| The number
of deaths in the United States attributed to the coronavirus disease is
116,979. There are more than 2.1 million certified coronavirus cases.
\|\| **1245 \| 2020-06-18**: The Supreme Court rules in a 5-4 decision
that President Trump may not immediately end Deferred Action for
Childhood Arrivals (DACA), saying that the Administration did not
provide “a reasoned explanation for its action”. \| Mary Elizabeth
Taylor, the first black woman to serve as assistant Secretary of State
for Legislative Affairs, resigns, stating President Trump’s “comments
and actions surrounding racial injustice…cut sharply against my core
values and conviction”. \| Kathryn Wheelbarger, a leading Defense
Department policy official in the Pentagon, resigns. \|\| **1246 \|
2020-06-19**: Geoffrey Berman, the top US attorney in the SDNY, declines
to leave his post after Attorney General William Barr announces his
removal and replacement earlier in the evening. \|\| **1247 \|
2020-06-20**: President Trump removes Geoffrey Berman as head attorney
for the SDNY after he refuses to step down the previous evening. \|
President Trump holds a rally in Tulsa, Oklahoma. Two Secret Service
agents at the event test positive for coronavirus; the Secret Service
later asks all agents who worked at the event to self-quarantine at home
for 14 days. \|\| **1249 \| 2020-06-22**: Kevin Hassett, chair of the
Council of Economic Advisers and the White House’s chief economist,
announces he will leave this summer after helping deal with the economic
disruptions of the continuing coronavirus pandemic. \|\| **1250 \|
2020-06-23**: President Trump visits Yuma, Arizona, along the southern
border and meets with Border Patrol personnel. \| President Trump holds
a rally with Students for Trump at the Dream City Megachurch in Phoenix,
Arizona \|\| **1251 \| 2020-06-24**: The number of deaths in the United
States attributed to the coronavirus disease is 121,978. There are more
than 2.3 million certified coronavirus cases. \| President Trump holds a
bilateral meeting and joint press conference with Polish president
Andrzej Duda at the White House. \| Aaron Zelinsky, a prosecutor on
Robert Mueller’s team, and John Elias, a career official in the
Antitrust Division at DOJ, appear before a House Judiciary Committee
hearing to give testimony about sentencing recommendations for Roger
Stone. \|\| **1252 \| 2020-06-25**: President Trump and First Lady
Melania Trump participate in the 70th anniversary of the start of the
Korean War. \| The Justice Act, a Republican-sponsored police overhaul
bill, falls short of the 60 votes of support required to advance the
bill after Senate Democrats block the bill and call it “woefully
inadequate”. \| In the House of Representatives, the George Floyd
Justice in Policing Act is approved by a vote of 236 to 181. \| The
Trump administration files a brief asking the Supreme Court to
invalidate the Affordable Care Act. \|\| **1253 \| 2020-06-26**: The New
York Times breaks a story about bounties being paid by Russia to Taliban
militants to kill American and coalition forces currently stationed in
Afghanistan. \|\| **1256 \| 2020-06-29**: Director of National
Intelligence John Ratcliffe, White House chief of staff Mark Meadows,
and national security adviser Robert C. O’Brien conduct a briefing for
GOP lawmakers at the White House concerning intelligence suggesting
Russia financed Taliban militants to target US and coalition troops.
\|\| **1258 \| 2020-07-01**: The United States-Mexico-Canada Agreement
(USMCA) comes into effect, replacing the North American Free Trade
Agreement (NAFTA). President Trump had campaigned on replacing NAFTA
with a new trade agreement. \| The number of deaths in the United States
attributed to the coronavirus disease is 127,461. There are more than
2.7 million certified coronavirus cases. \|\| **1259 \| 2020-07-02**:
President Trump launches “Made in America Week” at the White House by
showcasing products made in all fifty states. \|\| **1260 \|
2020-07-03**: President Trump hosts military personnel and their
families for a picnic and fireworks show at Mount Rushmore as part of
Independence Day celebrations. \|\| **1261 \| 2020-07-04**: President
Trump’s 2020 Salute to America occurs on Independence Day in Washington,
D.C., in addition to other events. \|\| **1264 \| 2020-07-07**:
President Trump informs Congress and the United Nations that the United
States will formally withdraw from the World Health Organization (WHO),
effective July 6, 2021. \|\| **1265 \| 2020-07-08**: President Trump
holds a bilateral meeting and joint press conference with Mexican
president Andres Manuel Lopez Obrador at the White House. \| The number
of deaths in the United States attributed to the coronavirus disease is
131,289. There are more than 3.0 million certified coronavirus cases.
\|\| **1266 \| 2020-07-09**: The Supreme Court rules 7-2 that House
Democrats may not access President Trump’s tax returns, but also
determined that he is not immune to a subpoena for his returns from a
New York prosecutor. \|\| **1267 \| 2020-07-10**: As Tropical Storm Fay
approaches, President Trump cancels Saturday plans for a campaign rally
in Portsmouth, New Hampshire. \| President Trump commutes the sentence
of Roger Stone, who was convicted of witness tampering and lying to
Congress about President Trump’s dealings with Russia to the Mueller
probe. \|\| **1270 \| 2020-07-13**: President Trump conducts a White
House panel composed of “people who have had positive interactions with
the police”. \|\| **1271 \| 2020-07-14**: President Trump gathers
reporters and press for a news conference in the Rose Garden at the
White House. \| The Trump administration orders hospitals to forego
sending all coronavirus patient information to the CDC and instead
submit it to a central database maintained by the Department of Health
and Human Services. \| President Trump signs the Hong Kong Autonomy Act
into law, placing sanctions on organizations that undermine Hong Kong’s
autonomy. \| President Trump announces new measures against China during
a 54-minute stream-of-consciousness press conference promising a vaccine
for the coronavirus, blaming China for “unleashing \[the coronavirus\]
upon the world” and various other topics from Joe Biden to crime in
“Democrat cities”.\[citation needed\] \|\| **1272 \| 2020-07-15**: The
number of deaths in the United States attributed to the coronavirus
disease is 136,356. There are more than 3.4 million certified
coronavirus cases. \|\| **1273 \| 2020-07-16**: The Trump administration
announces that hospitals will begin to send coronavirus patient
information to a central database maintained by the Department of Health
and Human Services rather than the CDC.\[citation needed\] \|\| **1278
\| 2020-07-21**: President Trump signs a presidential memorandum
requesting a ban of undocumented immigrants being counted in the 2020
census. \| President Trump announces plans to deploy federal law
enforcement officers to “Democrat” cities to quell ongoing protests over
racism and police brutality. Chicago Mayor Lori Lightfoot expressed
concern saying, “We don’t need federal agents without any insignia
taking people off the streets and holding them, I think, unlawfully.”
\|\| **1279 \| 2020-07-22**: Calling the protests in Portland, Oregon
“worse than Afghanistan,” President Trump defended the use of excessive
force against the peaceful protestors by officers in military camouflage
fatigues. \| The number of deaths in the United States attributed to the
coronavirus disease is 142,031. There are more than 3.9 million
certified coronavirus cases. \|\| **1281 \| 2020-07-24**: President
Trump signs four executive orders designed to lower prices on
prescription drugs. \|\| **1284 \| 2020-07-27**: National security
advisor Robert O’Brien tests positive for COVID-19. He has since been
working remotely. \|\| **1285 \| 2020-07-28**: Without any evidence that
mail-in ballots increase electoral fraud, President Trump continues to
suggest that the November election should be delayed. \|\| **1286 \|
2020-07-29**: The number of deaths in the United States attributed to
the coronavirus disease is 150,100. There are more than 4.3 million
certified coronavirus cases. \|\| **1287 \| 2020-07-30**: The U.S. GDP
indicator declined 9.5% during the second quarter of 2020, the most
drastic decline in 70 years.\[citation needed\] \| President Trump
suggests postponing the 2020 United States presidential election. \|\|
**1288 \| 2020-07-31**: President Trump says he plans to use
presidential authority to terminate the Chinese social media platform
TikTok from operating in the U.S. \|\| **1292 \| 2020-08-04**: The House
of Representatives Oversight Committee calls Postmaster General Louis
DeJoy to testify about recent delays and staff changes at the U.S.
Postal Service.\[citation needed\] \|\| **1293 \| 2020-08-05**:
President Trump meets with Governor of Arizona Doug Ducey in the Oval
Office. \| The number of deaths in the United States attributed to the
coronavirus disease is 157,297. There are more than 4.7 million
certified coronavirus cases. \| Stephen Akard, the acting State
Department’s inspector general, resigns after less than three months.
His deputy, Diana Shaw is appointed as the temporary acting inspector
general effective on August 7. \|\| **1294 \| 2020-08-06**: President
Trump signs executive orders banning the use of TikTok and WeChat in the
United States within 45 days if their Chinese parent companies refuse to
sell them as a result of national security concerns. \| President Trump
tours Whirlpool Corporation. \|\| **1296 \| 2020-08-08**: President
Trump signs an executive order and memoranda restoring coronavirus
relief pay for unemployed Americans at 400 per week. \|\| **1300 \|
2020-08-12**: The number of deaths in the United States attributed to
the coronavirus disease is 164,462. There are more than 5.1 million
certified coronavirus cases. \|\| **1301 \| 2020-08-13**: The Trump
Administration brokers a peace agreement between United Arab Emirates
and Israel, the first agreement between Israel and an Arab-Muslim
nation.\[citation needed\] \|\| **1302 \| 2020-08-14**: During a White
House press conference, President Trump mentions the Kevin Clinesmith
plea agreement, in which a former FBI lawyer admitted to altering an
email for the C.I.A. used by the agency to continue a secret wiretap on
the former Trump 2016 campaign adviser Carter Page. Trump claims
Clinesmith was “corrupt” and the plea deal was “just the beginning”.
\|\| **1305 \| 2020-08-17**: President Trump holds a campaign rally in
Mankato, Minnesota.\[citation needed\] \| President Trump holds a
campaign rally in Oshkosh, Wisconsin.\[citation needed\] \|\| **1306 \|
2020-08-18**: President Trump visits Yuma, Arizona, along the southern
border and meets with Border Patrol personnel. \| President Trump holds
a campaign rally in Yuma, Arizona.\[citation needed\] \|\| **1307 \|
2020-08-19**: The number of deaths in the United States attributed to
the coronavirus disease is 172,958. There are more than 5.5 million
certified coronavirus cases. \|\| **1308 \| 2020-08-20**: President
Trump holds a bilateral meeting with Iraqi prime minister Mustafa
Al-Kadhimi at the White House. \| President Trump holds a campaign rally
in Old Forge, Pennsylvania.\[citation needed\] \|\| **1312 \|
2020-08-24**: The four-day Republican National Convention begins. \|
President Trump accepts the nomination of the Republican Party for the
2020 United States presidential election. \|\| **1313 \| 2020-08-25**:
President Trump and Postmaster General Louis DeJoy are sued by the
states of New York and New Jersey over changes to postal service
operations such as the removal of mailboxes and mail sorting machines,
the curtailing of overtime hours and the implementation of additional
service reductions. \|\| **1314 \| 2020-08-26**: The number of deaths in
the United States attributed to the coronavirus disease is 179,215.
There are more than 5.8 million certified coronavirus cases. \|\| **1315
\| 2020-08-27**: President Trump delivers acceptance speech at the
Republican National Convention at the South Lawn of the White House.
Saying he “profoundly” accepted the nomination for a second term he
spoke for 70-minutes on the South Lawn of the White House. He repeatedly
misrepresented his record while leveling false or misleading attacks on
Democrats, blaming them for America’s problems. \| The House Foreign
Affairs Committee proceeds with contempt proceedings and a subpoena
against Mike Pompeo related to the State Department’s involvement in
attempts to link Joe Biden to corruption in Ukraine. \|\| **1316 \|
2020-08-28**: President Trump holds a campaign rally in Londonderry, New
Hampshire. \| Four people who attended the Republican National
Convention (which had just ended) test positive for COVID-19. \|\|
**1319 \| 2020-08-31**: John Ratcliffe, the Director of National
Intelligence, says his agency will no longer give Congress in-person
briefings about election security, citing concern over “unauthorized
disclosures of sensitive information” and will switch to written
updates. \|\| **1320 \| 2020-09-01**: While discussing the shooting of
Jacob Blake, President Trump compares police officers to golfers who
might “choke” while attempting a putt. \|\| **1321 \| 2020-09-02**:
President Trump participates in the 75th anniversary of the end of World
War II celebrations at the battleship North Carolina in Wilmington,
North Carolina, and designates the city as the first “American World War
II Heritage City”, which the secretary of the interior is allowed to
designate one city a year beginning in 2020. \| The number of deaths in
the United States attributed to the coronavirus disease is 184,564.
There are more than 6 million certified coronavirus cases. \| President
Trump urges North Carolina voters to cast two votes in the upcoming
presidential election, once by mail and then again in person, in order
to test his unsubstantiated claims that mail-in voting is prone to
fraud. \|\| **1322 \| 2020-09-03**: President Trump holds a campaign
rally in Latrobe, Pennsylvania. \|\| **1323 \| 2020-09-04**: President
Trump holds a trilateral meeting with Serbian president Aleksandar Vucic
and Kosovan prime minister Avdullah Hoti at the White House. \| A memo
to government agencies from the Office of Management and Budget calls on
all agencies to ceases funding for diversity training. labelling it
“divisive and anti-American propaganda”. \| President Trump disputes
reports in the Atlantic magazine that he has called dead American
service members “losers” and those signing to serve in the armed service
as “suckers”. \|\| **1327 \| 2020-09-08**: President Trump holds a
campaign rally in Winston-Salem, North Carolina and promotes voting by
mail and in person. \| The Department of Justice takes over the defense
of the President in a defamation lawsuit accusing him of sexual assault.
\|\| **1328 \| 2020-09-09**: The number of deaths in the United States
attributed to the coronavirus disease is 189,538. There are more than
6.3 million certified coronavirus cases. \| Christian Tybring-Gjedde, a
Norwegian politician, nominates President Trump for the Nobel Peace
Prize. \|\| **1329 \| 2020-09-10**: President Trump holds a news
conference and debates with journalists about the disparity between what
was said about the severity of the coronavirus in interviews with Bob
Woodward and his efforts to “play it down” to the American people. \|
President Trump holds a campaign rally in Freeland, Michigan. \|\|
**1330 \| 2020-09-11**: President Trump speaks at the Flight 93 National
Memorial to commemorate the 19th anniversary of the September 11
attacks. \| The Trump Administration brokers a peace agreement between
Bahrain and Israel, the second agreement between Israel and an
Arab-Muslim nation in less than one month.\[citation needed\] \|
President Trump presents the Medal of Honor to Sergeant Major Thomas
Payne. \| A member of the Swedish Parliament nominated President Trump
and the governments of Kosovo and Serbia for the 2021 Nobel Peace Prize
over economic cooperation and trade talks. \|\| **1331 \| 2020-09-12**:
President Trump addresses a crowd of supporters at a campaign rally in
Minden, Nevada. \|\| **1332 \| 2020-09-13**: President Trump holds a
roundtable at the Treasure Island Hotel and Casino in Las Vegas, Nevada.
\| President Trump addresses a crowd of supporters at a campaign rally
in Henderson, Nevada. \|\| **1333 \| 2020-09-14**: President Trump
participates in a briefing on the 2020 California wildfires with state
officials in McClellan Park, California. \| President Trump participates
in a ceremony honoring soldiers of the California National Guard for
their heroic actions during the 2020 California wildfires. \| President
Trump holds a roundtable in Phoenix, Arizona. \|\| **1334 \|
2020-09-15**: President Trump participates in the signing of the Abraham
Accord, normalizing relations between Israel and the United Arab
Emirates. \| President Trump participates in a town-hall meeting style
event with undecided Pennsylvania voters moderated by ABC’s George
Stephanopoulos. \|\| **1335 \| 2020-09-16**: Michael Caputo, Assistant
Secretary for Health and Human Services for Public Affairs, announces he
will take a 60-day leave of absence after he accused government
scientists of “sedition” and called on Trump’s supporters to arm
themselves ahead of the November 3rd election. \| President Trump holds
a press briefing in the James S. Brady Press Briefing Room, speaking on
multiple topics including the Coronavirus and Hurricane Sally. \| The
number of deaths in the United States attributed to the coronavirus
disease is 196,410. There are more than 6.6 million certified
coronavirus cases. \|\| **1336 \| 2020-09-17**: President Trump,
alongside United States Secretary of the Interior David Bernhardt and
United States Ambassador to Finland Robert Pence among others, announces
that the Finnish government has agreed to return Native American
artifacts and remains to the United States. The artifacts and remains
were taken in 1891 by explorer Gustaf Nordenskiold. All remains and
funerary objects were reinterned in Mesa Verde National Park. \|
President Trump presents a speech at the National Archives Building. He
speaks on multiple topics including American history and recent civil
unrest. \| President Trump addresses a crowd of supporters at a campaign
rally in Mosinee, Wisconsin. \| President Trump announces the formation
of The 1776 Commission a “patriotic education” commission. \|\| **1337
\| 2020-09-18**: President Trump presents the Legion of Merit to Emir
Sabah Al-Ahmad Al-Jaber Al-Sabah of Kuwait in a private ceremony at the
White House. \| The United States Department of Commerce announces that
apps TikTok and WeChat will be un-downloadable on all platforms in the
United States effective September 20, 2020. Users who have already
downloaded TikTok will still be able to use the app until November 13,
2020. \| President Trump approves an additional 13 billion in funding to
Puerto Rico to continue rebuilding efforts for Hurricane Maria damages.
\| The Centers for Disease Control and Prevention reverses a
controversial guidance stating that asymptomatic people should not
receive a COVID-19 test. \| President Trump holds a press conference in
the James S. Brady Press Briefing Room, speaking on multiple topics
including a COVID-19 vaccine and relief to Puerto Rico. \| Associate
Justice of the Supreme Court of the United States Ruth Bader Ginsburg
passes away at age 87 due to pancreatic cancer. \| President Trump
addresses a crowd of supporters at a campaign rally in Bemidji,
Minnesota. \|\| **1338 \| 2020-09-19**: An envelope addressed to the
White House is intercepted and found to be laced with the deadly toxin
ricin. Authorities say the envelope originated in Canada. \| President
Trump announces his support of the proposed deal for Walmart and Oracle
Corporation to take over TikTok’s cloud computing and acquire a combined
20% stake in the company. In response the United States Department of
Commerce delays the banning of the app until September 27, 2020. \|
President Trump addresses a crowd of supporters at a campaign rally in
Fayetteville, North Carolina. During the rally he announces that he is
planning on filling the vacant Supreme Court of the United States seat
left by the death of Ruth Bader Ginsburg, pledging that he will nominate
another woman. \|\| **1339 \| 2020-09-20**: Laurel Beeler, U.S.
Magistrate Judge of the United States District Court for the Northern
District of California, files a preliminary injunction effectively
barring the United States Department of Commerce’s plans to ban the
Chinese owned app WeChat from the American market. \| President Trump
approves a disaster declaration for the State of Alabama due to the
effects of Hurricane Sally. \|\| **1340 \| 2020-09-21**: President Trump
administration officials announce multiple new sanctions against the
Iranian Defense Ministry and Venezuelan President Nicolas Maduro. \|
Senior Judge of the United States District Court for the District of
Nevada James C. Mahan dismisses a lawsuit filed by President Trump
against the State of Nevada challenging the state’s recent mail-in
voting law. \| President Trump addresses a crowd of supporters at two
campaign rallies: One in Dayton, Ohio and the other in Swanton, Ohio.
\|\| **1341 \| 2020-09-22**: President Trump speaks virtually at the
General debate of the seventy-fifth session of the United Nations
General Assembly. \| The number of people who have died as a result of
the COVID-19 pandemic in the United States reaches 200,000 with 6.9
million cases total. \| Senator Mitt Romney announces his support to
push through a Supreme Court nominee, effectively giving President Trump
the majority he needs in the United States Senate to confirm a nominee.
\| President Trump addresses a crowd of supporters at a campaign rally
in Pittsburgh, Pennsylvania. \|\| **1342 \| 2020-09-23**: President
Trump honors veterans of the Bay of Pigs Invasion in a ceremony in the
East Room of the White House. He also takes the opportunity to announce
further sanctions against Cuba. \| A New York state judge orders Eric
Trump to appear at an under oath disposition on October 7, 2020 in
regards to financial crime investigations against the Trump
Organization. \| President Trump meets with multiple states Attorney
Generals in the Cabinet Room of the White House, speaking on the
“dangers of protecting Americans from censorship, cancel culture, and
consumer abuses inflicted by big tech companies.” \| President Trump
holds a news conference in the James S. Brady Press Briefing Room. In
response to a question about if he would committ to a peaceful transfer
of power he says, “Well, we’ll have to see what happens. You know that.
I’ve been complaining very strongly about the ballots. And the ballots
are a disaster,”. \|\| **1343 \| 2020-09-24**: President Trump and First
Lady Melania Trump pay respects to the late Justice Ruth Bader Ginsburg,
who is lying in repose in the Great Hall of the United States Supreme
Court Building. While paying their respects booing was heard from the
crowd, as well as chants of “honor her wish”. \| President Trump speaks
in Charlotte, North Carolina where he unveils his plan for the future of
health care. \| President Trump addresses a crowd of supporters at a
campaign rally in Jacksonville, Florida. \|\| **1344 \| 2020-09-25**:
President Trump holds a roundtable in Doral, Florida. \| President Trump
speaks at a forum, declaring that if re-elected he would fund more money
into institutions that lend to African-American businesses. He called
this “The Platinum Plan”. \| Lucy Koh, United States District Judge of
the Northern District of California, rules that the Trump Administration
is not allowed to end the 2020 United States Census early, and orders
the United States Census Bureau to continue through October 31st. \|
President Trump addresses a crowd of supporters at a campaign rally in
Newport News, Virginia. \|\| **1345 \| 2020-09-26**: President Trump
nominates Amy Coney Barrett as an Associate Justice of the Supreme Court
to fill the vacancy left by Ruth Bader Ginsburg, who died on September
18. \| President Trump addresses a crowd of supporters at a campaign
rally in Middletown, Pennsylvania. \| President Trump hosts a potential
superspreading event at the White House Rose Garden leading to the White
House COVID-19 outbreak. \|\| **1347 \| 2020-09-28**: President Trump
receives his third Nobel Peace Prize nomination from a group of
Australian law professors. \|\| **1348 \| 2020-09-29**: President Trump
and former Vice President Joe Biden participate in the first
presidential debate at Case Western Reserve University in Cleveland,
Ohio. The debate was moderated by Chris Wallace of Fox News. \|\| **1349
\| 2020-09-30**: President Trump addresses a crowd of supporters at a
campaign rally in Duluth, Minnesota. \| The Trump administration
announces plans to slash refugee admissions to the U.S. for 2021 to a
record low 15,000 refugees. down from a cap of 18,000 for 2020. \| Ronna
McDaniel, the chair of the Republican National Committee, tests positive
for coronavirus. \|\| **1350 \| 2020-10-01**: Hope Hicks, senior
counselor to President Trump, tests positive for coronavirus. She
traveled with President Trump to the debate in Cleveland on September 29
and to a rally in Minnesota on September 30. Although some White House
officials were aware of her diagnosis in the morning, “Trump still took
a trip to New Jersey for a fundraiser, and press secretary Kayleigh
McEnany still held a news briefing at the White House.” \|\| **1351 \|
2020-10-02**: President Trump tweets that both he and First Lady Melania
Trump had tested positive for coronavirus and would immediately
quarantine. Later that day, President Trump boarded a helicopter to
Walter Reed National Military Medical Center for treatment. \| President
Trump’s campaign manager Bill Stepien, RNC chairwoman Ronna Romney
McDaniel, and Senior Senator Mike Lee of Utah test positive for the
coronavirus. \|\| **1352 \| 2020-10-03**: Nick Luna, one of President
Trump’s closest personal attendants in the White House, tests positive
for coronavirus. \| Senators Thom Tillis, Mike Lee and Ron Johnson all
test positive for coronavirus. As a result, Senate Majority Leader Mitch
McConnell halts all Senate floor action for two weeks. \|\| **1353 \|
2020-10-04**: After President Trump rides in a motorcade around Walter
Reed Medical Center, a physician at the hospital says that every Secret
Service agent inside the vehicle will have to quarantine for 14 days.
\|\| **1354 \| 2020-10-05**: White House press secretary Kayleigh
McEnany announces she has coronavirus and will quarantine. Two of her
deputies also test positive. \| President Trump is discharged from the
hospital and returns to the White House in the evening. \|\| **1355 \|
2020-10-06**: Stephen Miller, senior political advisor to the president,
tests positive for the coronavirus. \|\| **1356 \| 2020-10-07**: Vice
President Mike Pence and Senator Kamala Harris participate in the only
vice presidential debate at University of Utah in Salt Lake City, Utah.
The debate was moderated by Susan Page of USA Today. \|\| **1357 \|
2020-10-08**: President Trump, having suddenly announced two days ago
that he was ending negotiations with lawmakers regarding a new economic
stimulus package, now says the talks are back on. \|\| **1358 \|
2020-10-09**: The Commission on Presidential Debates cancels the October
15 scheduled debate between the president and Joe Biden. President Trump
had refused to participate virtually. The third and final debate remains
scheduled for October 22. \|\| **1359 \| 2020-10-10**: President Trump
holds a rally on the South Lawn of the White House. Attendees’ travel
and lodging was paid for by Candace Owens’ group BLEXIT, which
encourages Black Americans to leave the Democratic Party. \|\| **1361 \|
2020-10-12**: President Trump addresses a crowd of supporters at a
campaign rally in Sanford, Florida. \|\| **1362 \| 2020-10-13**:
President Trump addresses a crowd of supporters at a campaign rally in
Johnstown, Pennsylvania. \|\| **1363 \| 2020-10-14**: President Trump
addresses a crowd of supporters at a campaign rally in Des Moines, Iowa.
\|\| **1364 \| 2020-10-15**: President Trump addresses a crowd of
supporters at a campaign rally in Greenville, North Carolina. \|
President Trump participates in a town-hall meeting style event with
undecided Florida voters instead of a planned second presidential
debate, which was cancelled after Trump refused to participate in a
virtual event. \|\| **1365 \| 2020-10-16**: The Federal Emergency
Management Agency (FEMA) rejects California’s request for federal aid
for the on-going forest fires. A FEMA spokesperson remarked that the
damage was “…not of such severity and magnitude to exceed the combined
capabilities of the state, affected local governments, voluntary
agencies and other responding federal agencies.” \| President Trump
addresses a crowd of supporters at two campaign rallies: Ocala, Florida
and Macon, Georgia. \|\| **1366 \| 2020-10-17**: President Trump
approves a federal disaster declaration for California’s wildfires after
having rejected the request the previous day. \| President Trump
addresses a crowd of supporters at two campaign rallies: Muskegon,
Michigan and Janesville, Wisconsin.\[citation needed\] \|\| **1367 \|
2020-10-18**: President Trump addresses a crowd of supporters at a
campaign rally in Carson City, Nevada.\[citation needed\] \|\| **1368 \|
2020-10-19**: President Trump addresses a crowd of supporters at two
campaign rallies in Arizona: Prescott and Tucson.\[citation needed\]
\|\| **1369 \| 2020-10-20**: President Trump addresses a crowd of
supporters at a campaign rally in Erie, Pennsylvania.\[citation needed\]
\|\| **1370 \| 2020-10-21**: President Trump addresses a crowd of
supporters at a campaign rally in Gastonia, North Carolina.\[citation
needed\] \|\| **1371 \| 2020-10-22**: President Trump and former Vice
President Joe Biden participate in the final presidential debate at
Belmont University in Nashville, Tennessee. The debate was moderated by
Kristen Welker of NBC.\[citation needed\] \|\| **1372 \| 2020-10-23**:
The Trump Administration brokers a peace agreement between Sudan and
Israel, the third agreement between Israel and an Arab-Muslim nation in
less than three months. \| President Trump addresses a crowd of
supporters at two campaign rallies in Florida: The Villages and
Pensacola. \|\| **1373 \| 2020-10-24**: President Trump addresses a
crowd of supporters at three campaign rallies: Lumberton, North
Carolina; Circleville, Ohio; and Waukesha, Wisconsin.\[citation needed\]
\|\| **1374 \| 2020-10-25**: CBS aired President Trump and Vice
President Pence’s interview for its news show 60 Minutes which was
filmed earlier in the week. President Trump was perturbed at host Lesley
Stahl asking “hard questions” and complained that former Vice President
Biden had received “softball questions”. Trump then walked off the set.
\| President Trump addresses a crowd of supporters at a campaign rally
in Manchester, New Hampshire.\[citation needed\] \|\| **1375 \|
2020-10-26**: President Trump addresses a crowd of supporters at three
campaign rallies in Pennsylvania: Allentown; Lititz; and
Martinsburg.\[citation needed\] \| In a vote of 52-48 the Senate
confirms Amy Coney Barrett as Supreme Court Justice. \| President Trump
attends the swearing in of Amy Coney Barrett as an Associate Justice of
the Supreme Court by Justice Clarence Thomas on the South Lawn of the
White House. \|\| **1376 \| 2020-10-27**: Amy Coney Barrett takes the
final judicial oath with Chief Justice John Roberts at the Supreme Court
of the United States thereby officially starting her tenure as Associate
Justice of the Supreme Court. \| President Trump addresses a crowd of
supporters at three campaign rallies: Lansing, Michigan; West Salem,
Wisconsin; and Omaha, Nebraska.\[citation needed\] \|\| **1377 \|
2020-10-28**: President Trump addresses a crowd of supporters at two
campaign rallies in Arizona: Bullhead City and Goodyear.\[citation
needed\] \|\| **1378 \| 2020-10-29**: President Trump addresses a crowd
of supporters at a campaign rally in Tampa, Florida.\[citation needed\]
\|\| **1379 \| 2020-10-30**: President Trump addresses a crowd of
supporters at three campaign rallies: Waterford Township, Michigan;
Green Bay, Wisconsin; and Rochester, Minnesota.\[citation needed\] \|\|
**1380 \| 2020-10-31**: President Trump addresses a crowd of supporters
at four campaign rallies in Pennsylvania: Newtown; Reading; Butler; and
Montoursville.\[citation needed\] \|\| **1381 \| 2020-11-01**: President
Trump addresses a crowd of supporters at five campaign rallies:
Washington Township, Michigan; Dubuque, Iowa; Hickory, North Carolina;
Rome, Georgia; and Opa-locka, Florida.\[citation needed\] \|\| **1382 \|
2020-11-02**: President Trump addresses a crowd of supporters at five
campaign rallies: Fayetteville, North Carolina; Scranton, Pennsylvania;
Traverse City, Michigan; Kenosha, Wisconsin; and Grand Rapids,
Michigan.\[citation needed\] \|\| **1383 \| 2020-11-03**: The 2020
United States presidential election is held. Trump carries 23 states and
213 electoral college points but no winner is declared on election
night. The interim results show Biden leading with 238 to 213 with many
swing states still being counted. \|\| **1384 \| 2020-11-04**: Despite
the lack of a clear winner, Trump declares victory at approximately 2am
claiming concerns about fraud and mail-in ballots. He states his
intention to request that the Supreme Court prevent any more ballots
from being counted. \|\| **1385 \| 2020-11-05**: Election winner still
remains to be called. Biden is leading with 264 electoral college points
compared to Trump’s 214. Nevada, Pennsylvania, Georgia, North Carolina
and Alaska are still yet to be called on this day. Trump leads in PA,
GA, NC, and AK but Biden’s lead in NV puts Trump’s re-election in
jeopardy. If Trump doesn’t overtake in NV he will lose re-election by 2
points with 268 electoral college points.
