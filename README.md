# Best-Price-Chart

In a bustling marketplace, a curious traveler named Arjun visited the food stalls, only to discover that the prices of the food items were missing from the charts. Determined to know the prices before making any decisions, Arjun searched the market’s official website and found k different versions of the price chart.
From his past adventures, Arjun knew that the correct price for an item is the highest price listed for it across all the charts. He also figured out that the most reliable, updated chart is the one with the most correct prices. If two or more charts have the same number of correct prices, the chart with the higher average price would be considered the most accurate.
Arjun needs your help to figure out which price chart is the most updated one so he can plan his purchases wisely.

def most_updated_menu(k, m, menus):
    max_prices = [max(menu[j] for menu in menus) for j in range(m)]
    
    best_menu = -1
    max_correct_prices = -1
    max_avg_price = -1.0
    
    for i in range(k):
        menu = menus[i]
        
        correct_prices_count = sum(1 for j in range(m) if menu[j] == max_prices[j])
        
        avg_price = sum(menu) / m
        
        if (correct_prices_count > max_correct_prices or
            (correct_prices_count == max_correct_prices and avg_price > max_avg_price)):
            best_menu = i + 1  
            max_correct_prices = correct_prices_count
            max_avg_price = avg_price
    
    return best_menu

k, m = map(int, input().split())
menus = [list(map(int, input().split())) for _ in range(k)]

print(most_updated_menu(k, m, menus))
