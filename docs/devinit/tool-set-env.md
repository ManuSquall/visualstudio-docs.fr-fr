---
title: set-env
description: outil devinit require-Set-env.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b1299686c086feda0c51689d72a676ddc4ff00dc
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400238"
---
# <a name="set-env"></a>set-env

L' `set-env` outil peut être utilisé pour définir des variables d’environnement à utiliser dans le processus actuel. Les variables d’environnement sont définies uniquement dans le processus actuel et seront utilisées par d’autres `devinit` outils si elles s’exécutent dans ce processus.

Cet outil utilise l’API .NET Core `Environment.SetEnvironment` et présente les mêmes limitations que cette API. Pour plus d’informations, consultez la [documentation](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) de `Environment.SetEnvironment` .

## <a name="usage"></a>Usage

| Nom                                         | Type   | Obligatoire | Valeur                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **commentaires**                                 | string | Non       | Propriété de commentaires facultative. Non utilisé.                                       |
| [**entrée**](#input)                          | string | Non       | Entrée de l’outil. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.               |
| [**additionalOptions**](#additional-options) | string | Non       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.  |

### <a name="input"></a>Entrée

L' `set-env` outil prend une chaîne unique comme entrée sur la `input` propriété. La chaîne doit être mise en forme sous la forme d’une chaîne de points-virgules (;) des paires clé/valeur délimitées (nom = valeur) et quatre actions possibles en fonction de la valeur de la `input` propriété.

| Action       | Entrée            | Description                                                                                                                                                              | Exemple             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **list all** | vide ou omis | Répertorie toutes les variables d’environnement actuelles.                                                                                                                              | `"input":""`        |
| **Liste 1** | string           | Répertorie la valeur d’une variable d’environnement spécifique par nom.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Définit la valeur d’une variable d’environnement en tant que paire de valeurs de clé. Ajoute une nouvelle variable d’environnement si elle n’est pas déjà présente ou définit la valeur d’une variable d’environnement existante. | `"input":"foo=bar"` |
| **delete**   | string           | Supprime une variable d’environnement existante en passant une chaîne de valeur vide.                                                                                            | `"input":"foo="`    |

Une `input` chaîne peut contenir une expansion de variable d’environnement `%userprofile%` , par exemple, qui est développée lorsque la valeur est lue.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

## <a name="usage-in-a-codespace"></a>Utilisation dans un codeSpace

Si vous utilisez un codeSpace, vous pouvez définir des variables d’environnement utilisées dans le codeSpace par le biais de customizating la `remoteEnv` propriété dans le [`.devcontainer.json`](/visualstudio/codespaces/reference/configuring) fichier.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "comments": "A sample dot-devinit file demonstrating the set-env tool.",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "comments": "To set an environment variable, set input to 'name=value'."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "To display the value of a single environment variable, set input to the name of the variable."
    },
    {
      "tool": "set-env",
      "comments": "To list all environment variables, pass no input."
    },
    {
      "tool": "set-env",
      "input": "foo=",
      "comments": "To delete an environment variable, pass input of 'name='."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "Trying to display a variable that doesn't exist results in a warning."
    },
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
      "comments": "Envrionment variable expansion is supported."
    },
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
      "comments": "Shows path manipulation. Note: Variables set here are not persisted."
    },
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
      "comments": "Restore path from saved copy."
    }
  ]
}
```