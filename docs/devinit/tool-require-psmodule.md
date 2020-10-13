---
title: require-psmodule
description: l’outil devinit requiert-PSModule.
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
ms.openlocfilehash: b855d8f3e9827d7b88f6d95bdf426cfb470b2bda
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959785"
---
# <a name="require-psmodule"></a>require-psmodule

L' `require-psmodule` outil permet d’installer un [module PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) à partir du [PowerShell Gallery](https://www.powershellgallery.com/) via [install-module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), afin qu’il puisse être utilisé dans les scripts PowerShell.

> [!TIP]
> Une fois qu’un module est installé, il doit toujours être importé dans un script à l’aide de [import-module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).

## <a name="usage"></a>Usage

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

## <a name="builtin-options"></a>Options builtin

L' `require-psmodule` outil définit un certain nombre d' `Install-Module` arguments de ligne de commande pour s’assurer que `Install-Module` peut s’exécuter sans affichage. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans le [module install-module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Nom         | Description                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Installe un module et remplace les messages d’avertissement relatifs aux conflits d’installation du module. Si un module portant le même nom existe déjà sur l’ordinateur, force autorise l’installation de plusieurs versions. Remplacera le module si un module existant portant le même nom et la même version existe. Force et AllowClobber peuvent être utilisés ensemble dans une commande Install-Module. |
| **-WhatIf**  | -L’indicateur WhatIf est ajouté lors de la transmission de la `devinit` commande.                                                                                                                                                                                                                                                                                                       |
| **-Verbose** | -L’indicateur verbose est ajouté lorsque verbose est passé pour la `devinit` commande.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the PowerShellGet module.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        },
        {
            "comments": "Installs the PowerShellGet module from a specific repository.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```