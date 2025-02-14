# ai_website_x
import openai
import datetime

openai.api_key = "ΒΑΛΕ_ΕΔΩ_ΤΟ_API_KEY"

def generate_post():
    today = datetime.date.today()
    prompt = f"Γράψε ένα νέο άρθρο για επενδύσεις με ημερομηνία {today}."
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    
    content = response["choices"][0]["message"]["content"]
    
    filename = f"_posts/{today}-ai-post.md"
    
    with open(filename, "w", encoding="utf-8") as file:
        file.write(f"---\ntitle: 'Αυτόματο άρθρο {today}'\ndate: {today}\n---\n\n{content}")

generate_post()
