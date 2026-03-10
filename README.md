| Signal | Category | Example | Primary Data | Purpose | AWS / boto3 APIs |
|------|------|------|------|------|------|
| Cost Anomaly | Cost Behavior | EC2 cost increased by $500 yesterday | FOCUS cost data + anomaly data | Detect sudden cost spikes | ce.get_anomalies(), ce.get_anomaly_monitors(), ce.get_cost_and_usage() |
| Forecast Risk | Cost Behavior | Spend projected to exceed forecast by $12k | FOCUS trend + forecast data | Predict overspending | ce.get_cost_forecast() |
| Budget Burn Risk | Cost Behavior | Budget will be exhausted in 8 days | FOCUS daily spend + budget definitions | Detect rapid budget consumption | budgets.describe_budgets(), budgets.describe_budget_performance_history() |
| Cost Acceleration | Cost Behavior | Compute cost increased 35% in 3 days | FOCUS daily spend | Detect accelerating spend | ce.get_cost_and_usage() |
| New Spend Detected | Cost Behavior | Redshift spend appeared this month | FOCUS service history | Detect new cost sources | ce.get_cost_and_usage(), ce.get_dimension_values() |
| Unallocated Spend | Allocation | 23% spend unallocated | FOCUS tags + resource tags | Identify missing ownership | ce.get_tags(), resourcegroupstaggingapi.get_resources() |
| Tagging Coverage Gap | Allocation | CostCenter missing on 42% of EC2 | FOCUS tags + resource tags | Improve tagging governance | resourcegroupstaggingapi.get_resources(), resourcegroupstaggingapi.get_tag_keys(), resourcegroupstaggingapi.get_tag_values() |
| Cost Ownership Drift | Allocation | Resources lost Team tag | Tag snapshots / history | Detect ownership changes | resourcegroupstaggingapi.get_resources() |
| Idle Resource Risk | Efficiency | Database idle for 7 days | Usage metrics + cost | Detect unused resources | cloudwatch.get_metric_data(), redshift.describe_clusters() |
| Overprovisioned Resource Risk | Efficiency | EC2 using only 12% CPU | CloudWatch metrics | Identify oversized infrastructure | cloudwatch.get_metric_data(), compute_optimizer.get_ec2_instance_recommendations() |
| Storage Growth Risk | Efficiency | Storage grew by 2TB in 3 days | Storage metrics + cost | Detect runaway storage growth | cloudwatch.get_metric_data() |
| Commitment Coverage Gap | Commitment | $300/day compute not covered | Commitment coverage + FOCUS spend | Identify savings opportunities | ce.get_savings_plans_coverage(), ce.get_reservation_coverage() |
| Commitment Waste | Commitment | Savings plan utilization 42% | Commitment utilization | Detect unused commitments | ce.get_savings_plans_utilization(), ce.get_reservation_utilization() |
| Spend Concentration Risk | Financial Risk | EC2 is 72% of spend | FOCUS service distribution | Identify single-service dependency | ce.get_cost_and_usage() |
| Cost Allocation Drift | Governance | Payments team share doubled | Tag distribution trend | Detect ownership shifts | ce.get_cost_and_usage() grouped by TAG |
| Account Spend Visibility Gap | Governance | New AWS account has spend but no mapped owner | Org metadata + cost | Detect unmapped accounts | organizations.list_accounts() |
| Rightsizing Opportunity | Efficiency | EC2 instance can be downsized | Cost + usage + optimizer recommendations | Identify savings actions | compute_optimizer.get_ec2_instance_recommendations(), trustedadvisor.list_recommendations() |
| Redshift Idle / Config Risk | Efficiency / Governance | Redshift cluster idle or missing owner tag | Redshift metadata + metrics | Detect warehouse waste | redshift.describe_clusters(), redshift.describe_tags(), cloudwatch.get_metric_data() |
