---
title: MSI-installation
description: outil devinit pour MsiExec.
ms.date: 10/13/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 98667c602272f22e7803647a688ee75d6c6cbd70
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402314"
---
# <a name="msi-install"></a>MSI-installation

L' `msi-install` outil est utilisé pour installer des `.msi` formats de fichier de package à l’aide de [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

## <a name="usage"></a>Usage

Si `input` est omis ou vide, l’outil génère une erreur.

| Nom                                         | Type   | Obligatoire | Valeur                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **commentaires**                                 | string | Non       | Propriété de commentaires facultative. Non utilisé.                                             |
| [**entrée**](#input)                          | string | Oui      | `msi` à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                      |
| [**additionalOptions**](#additional-options) | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                  |

### <a name="input"></a>Entrée

La propriété d’entrée est utilisée pour spécifier un chemin d’accès ou une URL vers un `.msi` fichier qui sera installé. Si le chemin d’accès à `.msi` est incorrect ou si l’URL ne pointe pas vers une adresse `.msi` directe, `msi-install` Notez que le package d’installation ne peut pas être ouvert.

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de additionalOptions. Ces arguments sont un relais direct vers les arguments utilisés par `msiexec` et sont définis dans la `msiexec` [documentation](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

### <a name="built-in-options"></a>Options intégrées

L’outil MSI-install définit un certain nombre d' `msiexec` arguments de ligne de commande pour s’assurer que MSI peut s’exécuter sans écran. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans la `msiexec` [documentation](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

| Nom          | Description                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Exécute une installation normale                                                                                                                                                                    | 
| /quiet        | Spécifie le mode silencieux sans intervention de l’utilisateur                                                                                                                                        | 
| /qn           | Indique qu’il n’y a aucune interface utilisateur pendant le processus d’installation                                                                                                                                           | 
| /passive      | Spécifie le mode sans assistance dans lequel l’installation affiche uniquement une barre de progression                                                                                                                    | 
| /l * V          | Active la journalisation et journalise toutes les informations, y compris les informations détaillées, dans un `devinit.log` fichier dans le dossier temporaire local de l’ordinateur. Si l’outil échoue, le chemin d’accès du fichier journal s’affiche.      | 
| /norestart    | Arrête le redémarrage de l’ordinateur une fois l’installation terminée, mais retourne un code de sortie 3010 si un redémarrage est nécessaire.                                                                  | 

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "comments": "Installs the 7-Zip MSI",
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
