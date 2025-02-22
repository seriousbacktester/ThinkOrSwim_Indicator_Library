declare upper;

input bbw_threshold = 0.3;
input BB_Length = 30;
input RSI_Length = 14;
input RSI_Threshold = 25;

def long1 = close > open;
def long2 = close[1] < open[1];
def long3 = close > high[1];
def long4 = low[1] < BollingerBands(length = BB_Length).LowerBand;
def long5 = RSI(length = RSI_Length) < RSI_Threshold within 2 bars;
def long6 = (((BollingerBands(length = BB_Length).UpperBand - BollingerBands(length=BB_Length).LowerBand)) / BollingerBands(length=BB_Length)) > bbw_threshold;

plot BB_RSI_Buy = long1 and long2 and long3 and long4 and long5 and long6;
BB_RSI_Buy.setPaintingStrategy(paintingStrategy.BOOLEAN_ARROW_UP);