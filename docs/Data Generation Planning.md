# Data Generation Planning
## As i can't use the real company data for a public project, so i have planned to generate a dataset from scratch to mimic the structure of a real IT service desk, and the data is split across multiple related tables instead of one flat file.

# Schema Design
## Agents Table
Column	            Type	                      Notes
agent_id	     serial, primary key	   auto-incrementing
agent_name	   text, not null	
team	         text, not null	       Service Desk, Network, EUC, SOC, Applications

### Categories Table
Column	                          Type	                            Notes
category_id	                 serial, primary key	               auto-incrementing
category_name	               text, not null, unique	
default_team	               text, not null	                must match a value in agents.team exactly

8 categories, each routed to a default team:
Category	                         Default Team
Laptop/Hardware Issue	                EUC
Peripheral Issue	                    EUC
Network Issue	                       Network
Software Issue	                      EUC
General User Issue	              Service Desk
Access Request	                  Service Desk
Security Incident	                   SOC
Application/System Down	          Applications

### Priority table

Column	                            Type	                             Notes
priority	                  text, primary key	                         P1–P4
description	                text, not null	                Critical, High, Medium, Low
sla_target_hours	          integer, not null	                      4, 8, 24, 72

SLA is deliberately tied to priority, not category — a Software Issue could be minor or severe depending on impact, so urgency (and therefore SLA) has to be independent of ticket type. This mirrors how real tools like ServiceNow and Jira Service Management structure SLAs.

#### Tickets  table - Fact table
Column	                                                 Type	                                                     Notes
ticket_id	                                          serial, primary key	
created_datetime	                                 timestamp, not null	
resolved_datetime	                                 timestamp, nullable	                                       NULL = still open
category_id	                        integer, not null, references categories(category_id)	
team	                                               text, not null	                                          copied from the logged category's default_team
agent_id	                              integer, not null, references agents(agent_id)	                       must belong to team above
priority	                                text, not null, references priority_sla(priority)	                  bumped up one level if is_vip
is_vip	                                             boolean, not null	
status	                                            text, not null	                                           Open, Resolved, Reopened
department	                                        text, not null	                                         Editorial, Marketing, Finance, HR, Broadcast Ops — the requesting user's department
is_misclassified	                                boolean, not null	                                         flags the deliberate 3–4% mismatched category rows

