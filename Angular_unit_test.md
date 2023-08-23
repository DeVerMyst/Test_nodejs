Les tests unitaires avec Angular sont effectués en utilisant le framework de test intégré à Angular, appelé Jasmine, ainsi qu'une couche d'outils de test supplémentaire fournie par Angular appelée Angular Testing Utilities. Jasmine est utilisé pour écrire les tests eux-mêmes, tandis que les Angular Testing Utilities fournissent des utilitaires pour simuler l'environnement Angular et pour manipuler les composants et services.

Voici comment vous pourriez réaliser des tests unitaires similaires avec Angular :

Supposons que vous ayez un composant `CalculatorComponent` avec des méthodes `add` et `subtract` que vous souhaitez tester.

**Fichier `calculator.component.ts` (Code du Composant à Tester) :**

```typescript
// calculator.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-calculator',
  template: '',
})
export class CalculatorComponent {
  add(a: number, b: number): number {
    return a + b;
  }

  subtract(a: number, b: number): number {
    return a - b;
  }
}
```

**Fichier `calculator.component.spec.ts` (Fichier de Test pour le Composant CalculatorComponent) :**

```typescript
// calculator.component.spec.ts
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { CalculatorComponent } from './calculator.component';

describe('CalculatorComponent', () => {
  let component: CalculatorComponent;
  let fixture: ComponentFixture<CalculatorComponent>;

  beforeEach(() => {
    TestBed.configureTestingModule({
      declarations: [CalculatorComponent],
    });

    fixture = TestBed.createComponent(CalculatorComponent);
    component = fixture.componentInstance;
  });

  it('should correctly add two numbers', () => {
    const result = component.add(2, 3);
    expect(result).toBe(5);
  });

  it('should correctly subtract two numbers', () => {
    const result = component.subtract(5, 3);
    expect(result).toBe(2);
  });
});
```

Dans cet exemple, nous avons créé un fichier de test `calculator.component.spec.ts` pour tester le composant `CalculatorComponent`.

- Nous utilisons Jasmine pour écrire les tests. Les fonctions `describe`, `beforeEach` et `it` sont des fonctions fournies par Jasmine pour organiser et écrire les tests.
- Nous utilisons `TestBed` fourni par Angular Testing Utilities pour configurer l'environnement de test et créer une instance du composant.
- Nous créons un `fixture` (fixation) pour le composant à tester, ce qui nous permet d'interagir avec lui et de l'inspecter.
- Nous utilisons les assertions Jasmine pour vérifier le comportement attendu des méthodes `add` et `subtract` du composant.

**Exécution des Tests :**

Pour exécuter les tests, vous pouvez utiliser la commande suivante dans le terminal :

```bash
ng test
```

Cela exécutera les tests du projet Angular à l'aide de Karma, un test runner utilisé par Angular CLI. Karma exécutera les tests dans un navigateur (ou d'autres environnements) et affichera les résultats dans la console.

Assurez-vous d'ajuster les chemins d'accès aux fichiers en fonction de votre propre structure de projet. Les concepts et les étapes sont similaires à ceux des tests avec Mocha et Chai, mais les utilitaires et la configuration spécifiques à Angular sont utilisés.

#### Arborescence des fichiers

```
project-folder/
├── src/
│   ├── app/
│   │   ├── calculator/
│   │   │   ├── calculator.component.ts
│   ├── main.ts
├── angular.json
├── tsconfig.json
├── tsconfig.app.json
├── tsconfig.spec.json
├── karma.conf.js
├── package.json
└── src/
    ├── app/
    │   ├── calculator/
    │   │   ├── calculator.component.ts
    │   │   ├── calculator.component.spec.ts
```

- **`src/app/calculator/`** : Ce dossier contient les fichiers associés au composant `CalculatorComponent`.

  - **`calculator.component.ts`** : Fichier du composant `CalculatorComponent` que vous souhaitez tester.
  - **`calculator.component.spec.ts`** : Fichier de tests unitaires pour le composant `CalculatorComponent`.

Voici comment le contenu du fichier `calculator.component.spec.ts` devrait être en relation avec la structure ci-dessus :

**Fichier `calculator.component.spec.ts` (Fichier de Test pour le Composant CalculatorComponent) :**

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { CalculatorComponent } from './calculator.component';

describe('CalculatorComponent', () => {
  let component: CalculatorComponent;
  let fixture: ComponentFixture<CalculatorComponent>;

  beforeEach(() => {
    TestBed.configureTestingModule({
      declarations: [CalculatorComponent],
    });

    fixture = TestBed.createComponent(CalculatorComponent);
    component = fixture.componentInstance;
  });

  it('should correctly add two numbers', () => {
    const result = component.add(2, 3);
    expect(result).toBe(5);
  });

  it('should correctly subtract two numbers', () => {
    const result = component.subtract(5, 3);
    expect(result).toBe(2);
  });
});
```

Assurez-vous que le fichier `calculator.component.spec.ts` est dans le même dossier que le composant `calculator.component.ts`. De plus, assurez-vous d'ajuster les chemins d'accès aux fichiers en fonction de votre propre structure de projet.