# CTS-HOMEWORK

						CTS 
					      Homework
				Right-BICEP and CORRECT

Method 1


1.1 Right-BICEP

private static final Pattern PASSWORD_PATTERN=
        Pattern.compile("^" +   "(?=.*[0-9])"+   "(?=.*[a-z])"+    "(?=.*[A-Z])"+   "(?=.*[@#$%^&*+=])"+
                "(?=\\S+$)"+   ".{6,}+" +  "$");


Button li = (Button) findViewById(R.id.bLogIn);
li.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        String email = _txtEmail.getText().toString();
        String passs = _txtPassword.getText().toString();
        if(email.length()==0) {   _txtEmail.setError("Email field can't be empty!"); }
        else if(passs.length()==0) {   _txtPassword.setError("Password field can't be empty!");  }
        else { SQLiteDatabase data = db.getReadableDatabase();
            Cursor res = data.rawQuery("Select * from register_table", null);
            if(res.moveToFirst()) {
                do {   if (res.getString(4).equals(email) && res.getString(3).equals(passs)) {
                        Intent intLogIn = new Intent(LoginFragment.this, HomePage.class);
                        startActivity(intLogIn); }
                }while(res.moveToNext());
            } } }});

• Right . Are the results right for the right input?
• B . Are all the boundary conditions CORRECT?
• I . Can you check inverse relationships?
• C . Can you cross-check results using other means? • E . Can you force error conditions to happen?
P . Are performance characteristics within bounds?

1.1Right

	To accomplish the right principle both email and password strings should be filled into the gaps. Also, those values will enter the database and must correspond with the values already put into the registration table. After you register, the data related to your account will be stored in the database, so, when you will log in, the app will automatically check if the values you introduce are already in the db or you have to go to the registration page.

1.1.2.  B - Boundary Conditions

	As you can observe, I included a boundary condition related to the password. So, in order to set a password for your account, this must contain numbers or letters or capital letters or other signs which will strengthen the password. All the conditions must be correct in order to login and go to the next page. Also, password must have 6 of those characters (letters, numbers, symbols).
	Also the two errors provider “Email field can’t be empty” and”Password field can’t be empty” tell us that both fields must me filled in order to go to the next steps.

1.1.3. I - Inverse Relationships

	In my case, in order to see the inverse relationship, I thought about filling the password field with a password that is less that 6 characters. If no conditions are introduces, the application will crack. Also, taking into consideration that both fields must be filled, when trying to go to the next app without having any email or password, there will appear 2 errors related to both of them.

1.1.4. C- Cross-Check (results using other means)

	Usually there is more than one way to choose a type of password for your account. So, in order to accomplish this principle, I would pick one algorithm over the others to write it . So, I can make a test that will allow the user introduce a password which has a capital letter, a number, a symbol and more than three other letters, for example A9!tttt. So, if the user won’t respect this kind of pattern , an error will be throw.

1.1.5. E -  Force Error Conditions ( can you force error condition to happen?)

	If I have a good path, I also can have a bad path, because error can happen all the time even if we think is impossible. One example related to the network availability and errors could be that the email can go into a black hole. Taking this step by step, one error could be that the email address of the registered user account is not unique so it must be thrown an exception, else, the email address will be added to the database. If everything worked good, the service method should return all the correct information.

1.1.6. P- Performance Characteristics

	I have to incorporate  general tests to make sure that the performance curve remains stable, so I have to design unit tests in order to see where the real problems are.
In order to accomplish this test, I can see in how much time this function will be finish without errors.



1.2 CORRECT

1.2.1.Conformance – Has the value the correct format/ Is the value valid ?
	In order to accomplish this point, I should make tests for:
		1.1 See if the email has the correct format (for example fghjk@yahoo.com)
		1.2 See if the password has the correct format after I set a pattern. As you can see in point 4 (C- Cross-Check) -> I can make a test that will allow the user introduce a password which has a capital letter, a number, a symbol and more than three other letters, for example A9!tttt.


1.2.2. Ordering – The set of values must be ordered or not ?

	I don’t have to any any validation regarding this part and the piece of code I presented.

1.2.3 Range – Is the value between acceptable limits (maxim and minim) ?

	Here I can make two tests:
		1.2.3.1. Set a minimum and maximum number of characters for email
		1.2.3.2. Set a minimum and maximum number of characters for password

1.2.4. Reference – Is the code referring external components which are NOT directly controlled?

	In my case, the code does not refer to external components which are not directly controlled.

1.2.5. Existence – Does the value exists (ex. non-null, non-zero, parte of a set, etc.)?

	Make tests for seeing if the email and passwords gaps are empty or not. They should not be empty in order to login to the app. 

1.2.6. Cardinality – Does the set of values has enough values?

	Each field must contain just one value: email and password.

1.2.7. Time (absolute or relative) – Is everything happing in order? At the right moment? In a limited time?

	Test if the login form makes the correlation with the database in the shortest time possible.


Method 2


2.1 Right-BICEP

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_chart_hw);
    xInput=(EditText)findViewById(R.id.etJava);
    yInput=(EditText)findViewById(R.id.etSQL);
    zInput=(EditText)findViewById(R.id.etC);
    qInput=(EditText)findViewById(R.id.etPython);
    chart = findViewById(R.id.chart);
    db=new DatabaseHelper(this);
    ArrayList<Entry> entries = new ArrayList<>();
    Cursor res=db.getAllDataGrades();
    res.moveToFirst();
    float s=0;
    float ss=0;
    float sss=0;
    float ssss=0;
    while(res.moveToNext())  {
        s=s+Float.parseFloat(res.getString(1));
        String val = String.valueOf(s);
        ss=ss+res.getFloat(2);
        sss=sss+res.getFloat(3);
        ssss=ssss+res.getFloat(4);   }
    entries.add(new Entry(1,s));
    entries.add(new Entry(2,ss));
    entries.add(new Entry(3,sss));
    entries.add(new Entry(4,ssss));
//more  lines of code related to making the chart
    };

	I didn’t make more separate functions for each thing I wanted to do, that is why I put here all the code included in the onCreate method.
	As you can see, here I made a chart. Taking into consideration the fact that this is a student application, where he can see his personal data, he can give his opinion about the university conditions ( teachers, courses, seminars) and he also, as you can see here, can complete a form where he can fill in the gaps how many homework did he complete for different subjects in order to make a big statistic with all the students.

• Right . Are the results right for the right input?
• B . Are all the boundary conditions CORRECT?
• I . Can you check inverse relationships?
• C . Can you cross-check results using other means? • E . Can you force error conditions to happen?
• P . Are performance characteristics within bounds?

Right

	To accomplish the right principle, I can make a function that won.t let the user drive to the next page unless he doesn’t fill all the gaps. Also, there can’t be negative numbers-> for example, if I had 2 tasks to complete for Java and I didn’t do anything, I can’t put “-2”, so I will put “0”. The system already know the numbers of task each student had to do.

2.  B - Boundary Conditions

	As you can observe, all numbers each user types are of float type so I can make tests in order to set this kind of type, not others like int, double, etc. Also, the four sums (s, ss, sss, ssss) must also be of float type and must be 0 at first. Other tests that I can make for each field is to not have empty ones. Each student must write a number between 0 and the total number of tasks he had to accomplish for a specific subject.

3. I - Inverse Relationships

	In my case, in order to see the inverse relationship, I thought about filling all the fields with letters or characters. I should make a test to specifically accept just float numbers, not other types of characters. Also, taking into consideration that all the four fields must be filled, when trying to go to the next app without having completed the Java, SQL,  C  and Python gaps, there can appear 4 errors related to them.

4. C- Cross-Check (results using other means)

	Usually there is more than one way to type a float number. So, in order to accomplish this principle, I would pick one algorithm over the others to write it . So, I can make a test that will allow the user introduce a number like “5.0” (the usually pattern for a float number), not to write just “5”. So, if the user won’t respect this kind of pattern , an error will be throw.


5. E -  Force Error Conditions ( can you force error condition to happen?)

	If I have a good path, I also can have a bad path, because error can happen all the time even if we think is impossible. One example related to the network availability and errors could be that the data regarding the homework page was already filled by the user, so I have to make a test that won’t let the user fill the form more than one time because the statistic will be a fail.

6. P- Performance Characteristics

	I have to incorporate  general tests to make sure that the performance curve remains stable, so I have to design unit tests in order to see where the real problems are.
In order to accomplish this test, I can see in how much time this function will be finish without errors.


2.2 CORRECT



2.2.1.Conformance – Has the value the correct format/ Is the value valid ?
	In order to accomplish this point, I should make tests for:
		2.2.1.1 See if the Java fields has the correct format (for example “5.0”, not “5”)
		2.2.1.2 See if the SQL fields has the correct format (for example “5.0”, not “5”)
		2.2.1.3 See if the C fields has the correct format (for example “5.0”, not “5”)
		2.2.1.4 See if the Python fields has the correct format (for example “5.0”, not “5”)



2.2.2. Ordering – The set of values must be ordered or not ?

	I don’t have to any any validation regarding this part and the piece of code I presented.

2.2.3 Range – Is the value between acceptable limits (maxim and minim) ?

	Here I can make 4 tests:
		2.2.3.1. Set a minimum and maximum float number for Java homework (between 0 and the total number of tasks given bu the teachers this current year)
		2.2.3.2. Set a minimum and maximum float number for SQL homework (between 0 and the total number of tasks given bu the teachers this current year)
		2.2.3.3. Set a minimum and maximum float number for C homework (between 0 and the total number of tasks given bu the teachers this current year)
		2.2.3.4. Set a minimum and maximum float number for Python homework (between 0 and the total number of tasks given bu the teachers this current year)

2.2.4. Reference – Is the code referring external components which are NOT directly controlled?

	In my case, the code does not refer to external components which are not directly controlled.

2.2.5. Existence – Does the value exists (ex. non-null, non-zero, parte of a set, etc.)?

	Make tests for seeing if the Java, SQL, C and Python gaps are empty or not. They should not be empty in order to take part in the statistics form.

2.2.6. Cardinality – Does the set of values has enough values?

	Each field must contain just one float number regarding the number of homework each student did in the current year.

2.2.7. Time (absolute or relative) – Is everything happing in order? At the right moment? In a limited time?

	Test if the statistics form makes the correlation with the database in the shortest time possible.
