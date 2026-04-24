postgres + redis

positions: user_id, event_id, choice(yes/no), shares, cost, status(open/closed/settled)
pool_state: event_id, yes_shares, no_shares, total_pool, updated_at
transactions: id, user_id, type, amount, ref_id, created_at

