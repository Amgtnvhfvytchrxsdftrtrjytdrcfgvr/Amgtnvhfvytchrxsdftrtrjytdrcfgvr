# Import necessary libraries
import numpy as np

# Function to calculate concrete volume
def calculate_concrete_volume(length, width, height):
    # Assuming a simple rectangular structure
    volume = length * width * height
    return volume

# Function to calculate concrete quantity based on mix design
def calculate_concrete_quantity(volume, cement_ratio, fine_aggregate_ratio, coarse_aggregate_ratio):
    # Assuming a standard mix design with ratios of cement, fine aggregate, and coarse aggregate
    cement_volume = volume * cement_ratio
    fine_aggregate_volume = volume * fine_aggregate_ratio
    coarse_aggregate_volume = volume * coarse_aggregate_ratio
    return cement_volume, fine_aggregate_volume, coarse_aggregate_volume

# Function to print results
def print_results(cement_volume, fine_aggregate_volume, coarse_aggregate_volume):
    print("Concrete Quantities:")
    print("Cement Volume:", cement_volume, "cubic meters")
    print("Fine Aggregate Volume:", fine_aggregate_volume, "cubic meters")
    print("Coarse Aggregate Volume:", coarse_aggregate_volume, "cubic meters")

# Function to save results to a file
def save_to_file(cement_volume, fine_aggregate_volume, coarse_aggregate_volume):
    with open("concrete_quantities.txt", "w") as file:
        file.write("Concrete Quantities:\n")
        file.write("Cement Volume: {} cubic meters\n".format(cement_volume))
        file.write("Fine Aggregate Volume: {} cubic meters\n".format(fine_aggregate_volume))
        file.write("Coarse Aggregate Volume: {} cubic meters\n".format(coarse_aggregate_volume))
    print("Results saved to concrete_quantities.txt")

# Main function
def main():
    # Input dimensions (in meters) from the user
    length = float(input("Enter length of the structure (m): "))
    width = float(input("Enter width of the structure (m): "))
    height = float(input("Enter height of the structure (m): "))

    # Input mix design ratios (assuming standard mix)
    cement_ratio = 0.20  # Cement ratio as per IS 456:2000
    fine_aggregate_ratio = 0.40  # Fine aggregate ratio as per IS 456:2000
    coarse_aggregate_ratio = 0.40  # Coarse aggregate ratio as per IS 456:2000

    # Calculate concrete volume
    volume = calculate_concrete_volume(length, width, height)

    # Calculate concrete quantity based on mix design
    cement_volume, fine_aggregate_volume, coarse_aggregate_volume = calculate_concrete_quantity(
        volume, cement_ratio, fine_aggregate_ratio, coarse_aggregate_ratio
    )

    # Print results
    print_results(cement_volume, fine_aggregate_volume, coarse_aggregate_volume)

    # Option to save results to a file
    save_option = input("Do you want to save the results to a file? (yes/no): ")
    if save_option.lower() == "yes":
        save_to_file(cement_volume, fine_aggregate_volume, coarse_aggregate_volume)

# Execute the main function
if __name__ == "__main__":
    main()
