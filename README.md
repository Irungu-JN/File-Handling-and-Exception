# File-Handling-and-Exception
def read_and_modify_file(input_filename, output_filename):
    """
    Reads a file, modifies its content, and writes the modified content to a new file.

    :param input_filename: str, name of the file to read
    :param output_filename: str, name of the file to write modified content
    """
    try:
        # Open and read the input file
        with open(input_filename, 'r') as infile:
            content = infile.readlines()
        
        # Modify the content (example: appending line numbers)
        modified_content = [f"{idx + 1}: {line}" for idx, line in enumerate(content)]

        # Write the modified content to the output file
        with open(output_filename, 'w') as outfile:
            outfile.writelines(modified_content)
        
        print(f"File '{input_filename}' has been successfully read and modified content saved to '{output_filename}'.")

    except FileNotFoundError:
        print(f"Error: The file '{input_filename}' does not exist.")
    except IOError:
        print(f"Error: Unable to read the file '{input_filename}' or write to '{output_filename}'.")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")


# Main program to get filenames from the user
if __name__ == "__main__":
    input_file = input("Enter the name of the file to read: ").strip()
    output_file = input("Enter the name of the file to write modified content to: ").strip()
    
    read_and_modify_file(input_file, output_file)
