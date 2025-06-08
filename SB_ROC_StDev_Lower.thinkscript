# thinkorswim thinkscript code
# Indicator: ROC StDev Lower
# Version: 1.0
# Description: A lower indicator that displays the Rate of Change (ROC)
#              and a dynamic threshold based on the standard deviation of the ROC.

declare lower;

# --- Input Parameters ---
input lengthROC = 14;
input priceSource = {
    default CLOSE,
    OPEN,
    HIGH,
    LOW
};
input lengthStDev = 200;
input multiplier = 2.0;

# --- Input Validation and Data Preparation ---
Assert(lengthROC >= 1, "'Length for ROC' must be 1 or greater.");
Assert(lengthStDev >= 1, "'Length for StDev' must be 1 or greater.");
Assert(multiplier > 0, "'Multiplier' must be greater than 0.");

def dataPrice;
switch (priceSource) {
case OPEN:
    dataPrice = open;
case HIGH:
    dataPrice = high;
case LOW:
    dataPrice = low;
case CLOSE:
    dataPrice = close;
}

# --- Core Calculations ---

# 1. Calculate Rate of Change (ROC)
def rocValue = RateOfChange(price = dataPrice, length = lengthROC);

# 2. Calculate Standard Deviation of the ROC
def stDevOfROC = StDev(data = rocValue, length = lengthStDev);

# 3. Calculate the dynamic threshold
def threshold = multiplier * (-stDevOfROC);

# --- Plotting Lines ---

# Plot ROC as a thin line
plot ROCLine = rocValue;
ROCLine.SetDefaultColor(Color.CYAN); # A visible color
ROCLine.SetLineWeight(1); # Thin line

# Plot the threshold as a thicker line
plot ThresholdLine = threshold;
ThresholdLine.SetDefaultColor(Color.YELLOW); # A contrasting color
ThresholdLine.SetLineWeight(2); # Thicker line

# --- Optional: Add a zero line for reference ---
plot ZeroLine = 0;
ZeroLine.SetDefaultColor(Color.GRAY);
ZeroLine.SetPaintingStrategy(PaintingStrategy.DASHES);

# --- End of Code ---
