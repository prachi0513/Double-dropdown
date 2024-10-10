# Double-dropdown
Created with CodeSandbox

import "./styles.css";
import { useState } from "react";

const countries = [
  { name: "India", value: "IN", cities: ["delhi", "Mumbai"] },
  { name: "Pakistan", value: "PK", cities: ["karanchi", "lahore"] },
  { name: "Bangaladesh", value: "BN", cities: ["Dhaka", "Melan"] },
];

export default function App() {
  const [city, setCity] = useState([]);

  const handleValueChange = (e) => {
    const current = e.target.value;
    const filterCity = countries.find((ite) => ite.value === current);
    if (filterCity) {
      setCity(filterCity.cities);
    } else {
      setCity([]);
    }
  };

  return (
    <div className="App">
      <select onChange={(e) => handleValueChange(e)}>
        {countries.map((country) => {
          return (
            <option key={country.name} value={country.value}>
              {country.name}
            </option>
          );
        })}
      </select>

      {city.length && (
        <select>
          {city.map((ite) => {
            return <option key={ite}>{ite}</option>;
          })}
        </select>
      )}
    </div>
  );
}
