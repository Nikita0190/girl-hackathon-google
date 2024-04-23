# girl-hackathon-google
def measure_latency_and_bandwidth(monitor_output):
    total_latency = 0
    total_transactions = 0
    total_cycles = 0
    start_cycle = None

    for row in monitor_output:
        if row['event'] == 'Rd Addr1':
            start_cycle = row['cycle']
        elif row['event'] == 'Data Addr1':
            end_cycle = row['cycle']
            latency = end_cycle - start_cycle
            total_latency += latency
            total_transactions += 1
        total_cycles += 1

    average_latency = total_latency / total_transactions
    total_bandwidth = total_transactions / total_cycles
