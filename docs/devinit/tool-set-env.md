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
ms.openlocfilehash: ce3876884061246d8ac1dbc1b211766903ea840a
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671738"
---
# <a name="set-env"></a>set-env

L' `set-env` outil peut être utilisé pour définir des variables d’environnement à utiliser dans le processus actuel. Les variables d’environnement sont définies uniquement dans le processus actuel et seront utilisées par d’autres `devinit` outils si elles s’exécutent dans ce processus.

Cet outil utilise l’API .NET Core `Environment.SetEnvironment` et présente les mêmes limitations que cette API. Pour plus d’informations, consultez la [documentation](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) de `Environment.SetEnvironment` .

## <a name="usage"></a>Utilisation

| Nom                                         | Type   | Obligatoire | Valeur                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **commentaires**                                 | string | No       | Propriété de commentaires facultative. Non utilisé.                                       |
| [**entrée**](#input)                          | string | No       | Entrée de l’outil. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.               |
| [**additionalOptions**](#additional-options) | string | No       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.  |

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

Si vous utilisez un codeSpace, vous pouvez définir des variables d’environnement utilisées dans le codeSpace en personnalisant la `remoteEnv` propriété dans le [`.devcontainer.json`](/visualstudio/codespaces/reference/configuring) fichier.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `set-env` l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.jssur qui définit une variable d’environnement, `foo` , sur value, `bar` :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
    }
  ]
}
```

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.jssur qui affichera la valeur d’une variable d’environnement :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo",
    }
  ]
}
```

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>.devinit.js, qui répertorie toutes les variables d’environnement :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
    }
  ]
}
```

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>.devinit.jssur cette opération supprimera une variable d’environnement :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=",
    }
  ]
}
```


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>.devinit.jssur qui utilise l’expansion de variables d’environnement :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.jssur qui définit une valeur de variable d’environnement à l’aide de la manipulation de chemin d’accès :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
    }
  ]
}
```

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.jssur qui restaure le chemin d’accès à partir d’une copie enregistrée :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
    }
  ]
}
```
