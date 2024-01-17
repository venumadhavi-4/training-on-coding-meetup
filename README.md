# 1 solution:
function countDevelopers(list) {
    const jsDevelopersFromEurope = list.filter(developer => 
        developer.language === 'JavaScript' && developer.continent === 'Europe'
    );

    return jsDevelopersFromEurope.length;
}
# 2 solution:
3function greetDevelopers(list) {
  for (var i=0; i<list.length; ++i)
    list[i]['greeting']='Hi '+list[i].firstName+', what do you like the most about '+list[i].language+'?';
  return list;
}
# 3 solution:
const isRubyComing = list => list.some(({ language }) => language === 'Ruby');
# 4 solution:
function getFirstPython(list) {
  var res = list.find(x => x.language=='Python');
  return res ? res.firstName+', '+res.country : 'There will be no Python developers';
}
# 5 solution:
function countLanguages(list) {
  let languageCount = {};

  list.forEach(dev => {
    const language = dev.language;
    languageCount[language] = (languageCount[language] || 0) + 1;
  });

  return languageCount;
}
# 6 solution:
function isSameLanguage(list) {
  for (var i = 0; i < list.length; i++) {
  if (list[0].language !== list[i].language) {
  return false;
  }
  }
  return true;
}
# 7 solution:
function findSenior(list) {
  return list.reduce((acc, dev) => {
    if(acc[0].age === dev.age) acc.push(dev);
    if(acc[0].age < dev.age) acc = [dev];
    
    return acc;
  }, [{ age: 0 }]);
}
# 8 solution:
function allContinents(list) {
  var continents = [];
  for (var i = 0; i<list.length; i++){
   if (continents.indexOf(list[i].continent) == -1){
   continents.push(list[i].continent);
   }
  }
  if (continents.length == 5){
  return true
  } else {
  return false
  }
}
# 9 solution:
function isAgeDiverse(list) {
  const ageGroups = ['teens', 'twenties', 'thirties', 'forties', 'fifties', 'sixties', 'seventies', 'eighties', 'nineties', 'centenarian'];

  return ageGroups.every(ageGroup => list.some(dev => isInAgeGroup(dev.age, ageGroup)));
}

// Function to determine if the given age is in the specified age group
function isInAgeGroup(age, ageGroup) {
  switch (ageGroup) {
    case 'teens':
      return age >= 10 && age <= 19;
    case 'twenties':
      return age >= 20 && age <= 29;
    case 'thirties':
      return age >= 30 && age <= 39;
    case 'forties':
      return age >= 40 && age <= 49;
    case 'fifties':
      return age >= 50 && age <= 59;
    case 'sixties':
      return age >= 60 && age <= 69;
    case 'seventies':
      return age >= 70 && age <= 79;
    case 'eighties':
      return age >= 80 && age <= 89;
    case 'nineties':
      return age >= 90 && age <= 99;
    case 'centenarian':
      return age >= 100;
    default:
      return false;
  }
}
# 10 solution:
function addUsername(list) {
  const currentYear = new Date().getFullYear();

  list.forEach(dev => {
    const birthYear = currentYear - dev.age;
    const username = `${dev.firstName.toLowerCase()}${dev.lastName[0].toLowerCase()}${birthYear}`;
    dev.username = username;
  });

  return list;
}
# 11 solution:
function getAverageAge(list) {
  const sumOfAges = list.reduce((sum, dev) => sum + dev.age, 0);
  const averageAge = Math.round(sumOfAges / list.length);

  return averageAge;
}
# 12 solution:
function findAdmin(list, lang) {
  return list.filter(dev => dev.language === lang && dev.githubAdmin === 'yes');
}
# 13 solution:
function isLanguageDiverse(list) {
    var ranking = list.reduce((p, c) => {
          p[c.language == "JavaScript" ? 0 : c.language == "Python" ? 1 : 2]++;
          return p;
        },
        [0, 0, 0]).sort((a, b) => b-a);

    return ranking[0] <= 2*ranking[2];
}
# 14 solution:
function orderFood(list) {
  // Use reduce to count the occurrences of each meal option
  const mealCount = list.reduce((count, developer) => {
    count[developer.meal] = (count[developer.meal] || 0) + 1;
    return count;
  }, {});

  return mealCount;
}
# 15 solution:
function findOddNames(list) {
  // Filter developers with odd ASCII representations for their first names
  return list.filter(developer => {
    const firstNameASCII = developer.firstName.split('').reduce((sum, char) => sum + char.charCodeAt(0), 0);
    return firstNameASCII % 2 !== 0;
  });
}
# 16 solution:
function askForMissingDetails(list) {
  // Filter developers with missing details
  return list.filter(developer => {
    const missingProperty = Object.keys(developer).find(key => developer[key] === null);
    if (missingProperty) {
      // Construct the question property
      developer.question = `Hi, could you please provide your ${missingProperty}.`;
      return true;
    }
    return false;
  });
}


