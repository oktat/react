# A useNavigate

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## A useNavigate használata

A useNavigate kampó a react-router-dom csomagban érkezik. Lehető teszi a direkt átirányítást a kódból.

### Importálás

```javascript
import { useNavigate } from "react-router-dom";
```

### Példányosítás

```javascript
const navigate = useNavigate();
```

### Használat

```javascript
navigate('/valami');
```

## Lehetésges példakód

src/components/Login.jsx:

```javascript
import { useState } from "react";
import { useNavigate } from "react-router-dom";

function Login() {
  const [user, setUser] = useState({
    username: '',
    password: ''
  });
  const navigate = useNavigate();

  const handleChange = (e) => {
    setUser({ ...user, [e.target.name]: e.target.value });
  }
  const handleSubmit = (e) => {
    e.preventDefault();
    if (user.username === 'admin' && user.password === 'admin') {      
      navigate('/profile');
    }
  }
  return (
    <div>
      <h1>Bejelentkezés</h1>
      
      <form className="loginForm">
        <fieldset className="bg-light p-3 rounded">          
          <div className="input">
            <label htmlFor="username"
            className='form-label'>Felhasználónév</label>
            <input type="text" name="username" id="username"
            className='form-control' 
            onChange={handleChange}
            value={user.username}
            />
          </div>
          <div className="input">
            <label htmlFor="password"
            className='form-label'>Jelszó</label>
            <input type="password" name="password" id="password"
            className='form-control' 
            onChange={handleChange} 
            value={user.password}
            />
          </div>
          
          <button type="submit"
          className='btn btn-primary mt-3'
          onClick={handleSubmit}>Belépés</button>
        </fieldset>
      </form>
      
    </div>
  )
}

export default Login
```
