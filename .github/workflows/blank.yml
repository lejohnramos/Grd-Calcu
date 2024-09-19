from flask import Flask, render_template_string, request

app = Flask(__name__)

# Combined calculation function
def calculate_final_grade(prelim, total_unpredictable):
    total = prelim * 0.2
    intermediate_total = total_unpredictable - total
    final_grade = intermediate_total / 0.8
    return final_grade

# HTML Template
html_template = '''
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grade Calculator</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
        }
        .container {
            text-align: center;
            max-width: 600px;
            width: 100%;
        }
        .result {
            font-size: 24px; 
            font-weight: bold;
            color: #333;
        }
        form {
            margin: 20px 0;
        }
        input[type="text"] {
            padding: 10px;
            font-size: 16px;
            width: 100%;
            max-width: 300px;
            margin: 10px 0;
        }
        input[type="submit"] {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Grade Calculator</h1>
        
        <form method="POST">
            <label for="prelim">Enter your prelim grade:</label>
            <input type="text" id="prelim" name="prelim" required><br><br>
            
            <label for="total_unpredictable">Enter your total unpredictable grade:</label>
            <input type="text" id="total_unpredictable" name="total_unpredictable" required><br><br>

            <input type="submit" value="Calculate"><br><br>
        </form>

        {% if final_grade is not none %}
            <h2 class="result">Total grade required for Midterm and Finalterm to pass: {{ final_grade }}</h2>
        {% endif %}
    </div>
</body>
</html>
'''

@app.route('/', methods=['GET', 'POST'])
def index():
    final_grade = None
    
    if request.method == 'POST':
        try:
            prelim = float(request.form['prelim'])
            total_unpredictable = float(request.form['total_unpredictable'])
            
            # Calculate final grade directly
            final_grade = calculate_final_grade(prelim, total_unpredictable)
            
        except ValueError:
            final_grade = "Invalid input, please enter valid numbers."
    
    return render_template_string(html_template, final_grade=final_grade)

if __name__ == '__main__':
    app.run(debug=True)
