# Election Audit
## Overview of Election Audit
Tom, a Colorado board of elections employee, needs tabulated results for a U.S. congressional precinct in Colorado election audit. The election commission has requested an analysis of the voter turnout for each country, the percentage of votes from each county out of the total count, and the county with the highest turnout with a program we created in Python. We will use images and examples of our code to demonstrate the the election-audit results.

## Election-Audit Results
#### How many votes were cast in this congressional election?
![image](https://user-images.githubusercontent.com/92180070/198178030-ba0e8ede-2b96-4455-b9f7-348ecc65a21e.png)

  ```Initialize a total vote counter.
  total_votes = 0

  # For each row in the CSV file.
  for row in reader:

  # Add to the total vote count
  total_votes = total_votes + 1
  # Print the final vote count (to terminal)
  election_results = (
  f"\nElection Results\n"
  f"-------------------------\n"
  f"Total Votes: {total_votes:,}\n"
  f"-------------------------\n\n"
  f"County Votes:{county_votes}\n")
  print(election_results, end="")
  txt_file.write(election_results)
  ````

#### Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct
![image](https://user-images.githubusercontent.com/92180070/198178064-d984e362-25ff-4a82-94c7-98c8c0239133.png)

  ```1: Create a county list and county votes dictionary.
  county_list = []
  county_votes ={}

  # 6a: Write a for loop to get the county from the county dictionary.
      for county in county_list:
         # 6b: Retrieve the county vote count.
         county_vote =county_votes.get(county)

         # 6c: Calculate the percentage of votes for the county.
         county_vote_percentage = float(county_vote) / float(total_votes) *100

         # 6d: Print the county results to the terminal.
          county_results = f"{county}: {county_vote_percentage:.1f}% ({county_vote:,})\n"
          # 6e: Save the county votes to a text file.
          txt_file.write(county_results)
```

 
#### Which county had the largest number of votes?
![image](https://user-images.githubusercontent.com/92180070/198178084-2350ad07-a2ec-4f45-bfdc-712a1bf876ef.png)

  ```# 6f: Write an if statement to determine the winning county and get its vote count.
  if (county_vote > largest_county_voter_turnout) and (
  county_vote_percentage > largest_county_percentage
  ):
  largest_county_voter_turnout = county_vote
  largest_county_percentage = county_vote_percentage
  largest_county = county
  # 7: Print the county with the largest turnout to the terminal.
  winning_county_summary = (
  f"-------------------------\n"
  f"Winner: {largest_county}\n"
  f"Winning Vote Count: {largest_county_voter_turnout:,}\n"
  f"-------------------------\n")
  print(winning_county_summary)
  ```
#### Provide a breakdown of the number of votes and the percentage of the total votes each candidate received. 
![image](https://user-images.githubusercontent.com/92180070/198178109-f44e2345-a44f-46c6-839b-b7b6770740f3.png)

  ```# For each row in the CSV file.
  for row in reader:

  # Add to the total vote count
  total_votes = total_votes + 1

  # Get the candidate name from each row.
  candidate_name = row[2]

  # 3: Extract the county name from each row.
  county_name = row[1]

  # If the candidate does not match any existing candidate add it to
  # the candidate list
  if candidate_name not in candidate_options:

  # Add the candidate name to the candidate list.
  candidate_options.append(candidate_name)

  # And begin tracking that candidate's voter count.
  candidate_votes[candidate_name] = 0
  ```
#### Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
![image](https://user-images.githubusercontent.com/92180070/198178126-d2b964c2-1973-4f46-80f2-a66f2cfb1ed1.png)


 ``` # Add a vote to that candidate's count
  candidate_votes[candidate_name] += 1
  # Determine winning vote count, winning percentage, and candidate.
  if (votes > winning_count) and (vote_percentage > winning_percentage):
  winning_count = votes
  winning_candidate = candidate_name
  winning_percentage = vote_percentage

  # Print the winning candidate (to terminal)
  winning_candidate_summary = (
  f"-------------------------\n"
  f"Winner: {winning_candidate}\n"
  f"Winning Vote Count: {winning_count:,}\n"
  f"Winning Percentage: {winning_percentage:.1f}%\n"
  f"-------------------------\n")
  print(winning_candidate_summary)```
  ```
## Election-Audit Summary
  Maximize returns and minimize risks by utilizing our program that can be utilized for any election. Automating repetitive tasks, like counting votes and determining a winner, will optimize productivity, while avoiding man-made errors. With minimal altercations to our program, we can audit congressional districts, senatorial districts, and local elections. For example, by gathering the data from the congressional districts election results we can determine the winner. All we would need to do is update where we extract the congressional candidates. We could easily determine which senatorial districts had the largest turnout by updating the county name variable to district name. To summarize, our program will save the election commission time, money, and liabilities for years to come.
