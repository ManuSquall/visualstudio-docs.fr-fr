---
title: require-psmodule
description: l’outil devinit requiert-PSModule.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: cdb37bf4e714cfc25e5bf82354856fd4d3d63e87
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672699"
---
# <a name="require-psmodule"></a>require-psmodule

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.


L' `require-psmodule` outil permet d’installer un [module PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) à partir du [PowerShell Gallery](https://www.powershellgallery.com/) via [install-module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), afin qu’il puisse être utilisé dans les scripts PowerShell.

> [!TIP]
> Une fois qu’un module est installé, il doit toujours être importé dans un script à l’aide de [import-module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                   |
| [**entrée**](#input)                              | string | Oui      | Package (s) à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                       |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.              |

### <a name="input"></a>Entrée

La `input` propriété doit être le `Name` du module PowerShell à installer. Vous pouvez trouver la liste des modules PowerShell disponibles en effectuant une recherche dans la [PowerShell Gallery](https://www.powershellgallery.com/).

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont transmises directement à la commande [install-module](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) et sont documentées sur [Microsoft docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7).

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-psmodule` outil est l’erreur telle qu’elle est `input` requise.

### <a name="built-in-options"></a>Options intégrées

L' `require-psmodule` outil définit un certain nombre d' `Install-Module` arguments de ligne de commande pour s’assurer que `Install-Module` peut s’exécuter sans affichage. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans le [module install-module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Nom         | Description                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Installe un module et remplace les messages d’avertissement relatifs aux conflits d’installation du module. Si un module portant le même nom existe déjà sur l’ordinateur, force autorise l’installation de plusieurs versions. Remplacera le module si un module existant portant le même nom et la même version existe. Force et AllowClobber peuvent être utilisés ensemble dans une commande Install-Module. |
| **-WhatIf**  | -L’indicateur WhatIf est ajouté lors de la transmission de la `devinit` commande.                                                                                                                                                                                                                                                                                                       |
| **-Verbose** | -L’indicateur verbose est ajouté lorsque verbose est passé pour la `devinit` commande.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `require-psmodule` l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-powershellget-module"></a>.devinit.jssur qui installe le module PowerShellGet :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-powershellget-module-from-a-specific-repository"></a>.devinit.jssur qui installe le module PowerShellGet à partir d’un référentiel spécifique :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```