Movie Rating Prediction – מטלת סיום חלק 2
קורס: Machine Learning | אוניברסיטת אריאל
מרצה: Chen Hajaj
שמות חברי הצוות: שיראל חדד ועינב ינון
קישור ל-GitHub: machine-learning

תיאור הפרויקט
פרויקט זה עוסק בניבוי דירוג סרטים (IMDb averageRating) באמצעות שיטות למידת מכונה.
המודל מבוסס על פיצ'רים היסטוריים של במאים ושחקנים, מאפייני הסרט (ז'אנר, שנה, אורך) ויחסי Runtime יחסיים לפי ז'אנר.

מבנה הקבצים
├── notebook.ipynb          # המחברת הראשית עם כל הקוד
├── dataset.csv             # דאטת הסרטים הראשית
├── title.crew.tsv.gz       # נתוני במאים מ-IMDb
├── model.pkl               # המודל השמור (Random Forest Pipeline)
├── requirements.txt        # כל הספריות שבהן השתמשנו, עם גרסאות
└── README.md               # קובץ זה
ספריות נדרשות
ראה קובץ requirements.txt להתקנה מלאה:

numpy>=2.4.4
pandas>=3.0.2
matplotlib>=3.10.8
seaborn>=0.13.2
scikit-learn>=1.8.0
joblib>=1.5.3
ipython
התקנה והרצה
1. התקנת ספריות
pip install -r requirements.txt
2. הרצת המחברת
jupyter notebook notebook.ipynb
יש להריץ את התאים לפי הסדר – הפונקציות ההיסטוריות תלויות בסדר הרצה.

תיאור קצר של המודל
פיצ'רים
פיצ'ר	תיאור
startYear	שנת יציאת הסרט
runtimeMinutes	אורך הסרט בדקות
num_genres	מספר הז'אנרים
is_too_short / is_too_long	דגל סרט קצר/ארוך חריג
relative_runtime_by_genre	אורך יחסי לחציון הז'אנר (היסטורי)
director_past_avg	ממוצע דירוגי הבמאי בסרטים קודמים
director_genre_past_avg	ממוצע דירוגי הבמאי בז'אנר הספציפי
director_genre_count	מספר סרטים קודמים של הבמאי בז'אנר
is_new_director	האם הבמאי חדש (ללא היסטוריה)
max_actors_past_experience	ניסיון השחקן המנוסה ביותר בסרט
is_new_actors	האם כל השחקנים חדשים
מודלים שנבדקו
Elastic Net – מודל לינארי עם רגולריזציה L1+L2
Random Forest – מודל אנסמבל (נבחר כמודל הסופי)
הערכת ביצועים
עם מניעת זליגת נתונים 10-Fold Cross Validation אימות בשיטת הפיצרים מבוססי חישובים תלויים רק בנתוני עבר ורק על סט האימון
הערות חשובות
יש להריץ את כל התאים לפי הסדר – חלק מהפונקציות מסתמכות על משתנים גלובליים
חישוב הפיצ'רים ההיסטוריים (calculate_historical_features) עשוי לקחת מספר דקות על הדאטה המלאה
המודל הסופי נשמר כ-model.pkl ונטען עם joblib.load('model.pkl')
