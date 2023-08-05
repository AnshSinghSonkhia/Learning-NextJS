# Learning-NextJS
Learning NextJS


## This table summarizes the different use cases for Server and Client Components:

<table>
   <thead>
      <tr>
         <th>What do you need to do?</th>
         <th>Server Component</th>
         <th>Client Component</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>Fetch data</td>
         <td>Yes 🟢</td>
         <td>No 🔴</td>
      </tr>
      <tr>
         <td>Access backend resources (directly)</td>
         <td>Yes 🟢</td>
         <td>No 🔴</td>
      </tr>
      <tr>
         <td>Keep sensitive information on the server (access tokens, API keys, etc)</td>
         <td>Yes 🟢</td>
         <td>No 🔴</td>
      </tr>
      <tr>
         <td>Keep large dependencies on the server / Reduce client-side JavaScript</td>
         <td>Yes 🟢</td>
         <td>No 🔴</td>
      </tr>
      <tr>
         <td>Add interactivity and event listeners (onClick(), onChange(), etc)</td>
         <td>No 🔴</td>
         <td>Yes 🟢</td>
      </tr>
      <tr>
         <td>Use State and Lifecycle Effects (useState(), useReducer(), useEffect(), etc)</td>
         <td>No 🔴</td>
         <td>Yes 🟢</td>
      </tr>
      <tr>
         <td>Use browser-only APIs</td>
         <td>No 🔴</td>
         <td>Yes 🟢</td>
      </tr>
      <tr>
         <td>Use custom hooks that depend on state, effects, or browser-only APIs</td>
         <td>No 🔴</td>
         <td>Yes 🟢</td>
      </tr>
      <tr>
         <td>Use React Class components</td>
         <td>No 🔴</td>
         <td>Yes 🟢</td>
      </tr>
   </tbody>
</table>
