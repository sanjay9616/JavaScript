<h1>Javascript Interview Questions and Answers</h1>

<ol>

  <li>
    <details>
        <summary><b>What is the difference between Call, Apply and Bind?</b></summary>
        <p>
        <b>Call:</b> The call() method invokes a function with a given <b>this</b> value and arguments provided one by one.
<pre>
<code>
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
    console.log(greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2);
}

invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How are you?
invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How are you?
</code>
</pre>
      </p>
    </details>
  </li>

  <li>
    <details>
        <summary><b>Tell me about yourself22.</b></summary>
    </details>
  </li>

</ol>