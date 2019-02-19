---
title: '&lt;InstallChecks&gt; élément (programme d’amorçage) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3556c36e00ac092c1ebb3af4e6d09921fcd11233
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023575"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; élément (programme d’amorçage)
Le `InstallChecks` élément prend en charge le démarrage d’une variété de tests sur l’ordinateur local pour vous assurer que toutes les conditions préalables requises pour une application ont été installés.  

## <a name="syntax"></a>Syntaxe  

```xml  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  

## <a name="assemblycheck"></a>AssemblyCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`. Pour chaque instance de `AssemblyCheck`, le programme d’amorçage permet de garantir que l’assembly identifié par l’élément existe dans le global assembly cache (GAC). Il ne contient aucun élément et a les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Le nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous le `InstallConditions` élément, qui est un enfant de le `Command` élément. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obligatoire. Le nom qualifié complet de l’assembly à vérifier.|  
|`PublicKeyToken`|Obligatoire. La forme abrégée de la clé publique associé à cet assembly un nom fort. Tous les assemblys stockés dans le GAC doivent avoir un nom, une version et une clé publique.|  
|`Version`|Obligatoire. Version de l'assembly.<br /><br /> Le numéro de version est au format \< *opus*>.\< *version mineure*>.\< *générer version*>.\< *version de révision*>.|  
|`Language`|Optionnel. La langue d’un assembly localisé. La valeur par défaut est `neutral`.|  
|`ProcessorArchitecture`|Optionnel. Le processeur d’ordinateur ciblé par cette installation. La valeur par défaut est `msil`.|  

## <a name="externalcheck"></a>ExternalCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`. Pour chaque instance de `ExternalCheck`, le programme d’amorçage exécute le programme externe nommé dans un processus séparé et stocker son code de sortie dans la propriété indiquée par `Property`. `ExternalCheck` est utile pour l’implémentation de contrôles de dépendance complexes, ou lorsque la seule façon de vérifier l’existence d’un composant consiste à instancier.  

 `ExternalCheck` ne contient aucun élément et a les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Le nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous le `InstallConditions` élément, qui est un enfant de le `Command` élément. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obligatoire. Le programme externe à exécuter. Le programme doit faire partie du package de distribution le programme d’installation.|  
|`Arguments`|Optionnel. Fournit des arguments de ligne de commande à l’exécutable nommé par `PackageFile`.|  

## <a name="filecheck"></a>FileCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`. Pour chaque instance de `FileCheck`, le programme d’amorçage déterminera si le fichier nommé existe et retourner le numéro de version du fichier. Si le fichier n’a pas un numéro de version, le programme d’amorçage définit la propriété nommée par `Property` à 0. Si le fichier n’existe pas, `Property` n’est pas définie pour n’importe quelle valeur.  

 `FileCheck` ne contient aucun élément et a les attributs suivants.  


| Attribut | Description |
|-----------------| - |
| `Property` | Obligatoire. Le nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous le `InstallConditions` élément, qui est un enfant de le `Command` élément. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Obligatoire. Le nom du fichier à rechercher. |
| `SearchPath` | Obligatoire. Le disque ou le dossier dans lequel rechercher le fichier. Cela doit être un chemin d’accès relatif si `SpecialFolder` est assigné ; sinon, il doit être un chemin d’accès absolu. |
| `SpecialFolder` | Optionnel. Un dossier qui a une signification particulière pour Windows ou à [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. La valeur par défaut consiste à interpréter `SearchPath` comme un chemin d’accès absolu. Les valeurs valides sont les suivantes :<br /><br /> `AppDataFolder`. Le dossier application data pour ce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de l’application ; spécifiques à l’utilisateur actuel.<br /><br /> `CommonAppDataFolder`. Le dossier de données d’application utilisé par tous les utilisateurs.<br /><br /> `CommonFilesFolder`. Le dossier fichiers communs pour l’utilisateur actuel.<br /><br /> `LocalDataAppFolder`. Le dossier de données pour les applications non itinérant.<br /><br /> `ProgramFilesFolder`. Le dossier Program Files standard pour les applications 32 bits.<br /><br /> `StartUpFolder`. Le dossier qui contient toutes les applications lancées au démarrage du système.<br /><br /> `SystemFolder`. Le dossier qui contient des DLL système 32 bits.<br /><br /> `WindowsFolder`. Le dossier qui contient l’installation du système Windows.<br /><br /> `WindowsVolume`. Le lecteur ou la partition qui contient l’installation du système Windows. |
| `SearchDepth` | Optionnel. La profondeur à partir duquel rechercher des sous-dossiers pour le fichier nommé. La recherche respecte la profondeur en premier. La valeur par défaut est 0, ce qui limite la recherche sur le dossier de niveau supérieur spécifié par `SpecialFolder` et **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`. Pour chaque instance de `MsiProductCheck`, le programme d’amorçage vérifie si l’installation de Microsoft Windows Installer spécifiée a exécuté jusqu'à son terme. La valeur de propriété est définie selon l’état du produit installé. Une valeur positive indique que le produit est installé, 0 ou -1 indique qu’il n’est pas installé. (Voir la fonction du Kit de développement Windows Installer MsiQueryFeatureState pour plus d’informations.) . Si le programme d’installation de Windows n’est pas installé sur l’ordinateur, `Property` n’est pas définie.  

 `MsiProductCheck` ne contient aucun élément et a les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Le nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous le `InstallConditions` élément, qui est un enfant de le `Command` élément. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obligatoire. Le GUID pour le produit installé.|  
|`Feature`|Optionnel. Le GUID pour une fonctionnalité spécifique de l’application installée.|  

## <a name="registrycheck"></a>RegistryCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`. Pour chaque instance de `RegistryCheck`, le programme d’amorçage vérifie si la clé de Registre spécifiée existe, ou si elle a la valeur indiquée.  

 `RegistryCheck` ne contient aucun élément et a les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Le nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous le `InstallConditions` élément, qui est un enfant de le `Command` élément. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatoire. Nom de la clé de Registre.|  
|`Value`|Optionnel. Le nom de la valeur de Registre à récupérer. La valeur par défaut consiste à retourner le texte de la valeur par défaut. `Value` doit être une chaîne ou une valeur DWORD.|  

## <a name="registryfilecheck"></a>RegistryFileCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`. Pour chaque instance de `RegistryFileCheck`, le programme d’amorçage récupère la version du fichier spécifié, essayant d’abord de récupérer le chemin d’accès au fichier à partir de la clé de Registre spécifiée. Cela est particulièrement utile si vous souhaitez rechercher un fichier dans un répertoire spécifié en tant que valeur dans le Registre.  

 `RegistryFileCheck` ne contient aucun élément et a les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Le nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous le `InstallConditions` élément, qui est un enfant de le `Command` élément. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatoire. Nom de la clé de Registre. Sa valeur est interprétée comme le chemin d’accès vers un fichier, à moins que le `File` attribut est défini. Si cette clé n’existe pas, `Property` n’est pas définie.|  
|`Value`|Optionnel. Le nom de la valeur de Registre à récupérer. La valeur par défaut consiste à retourner le texte de la valeur par défaut. `Value` doit être une chaîne.|  
|`FileName`|Optionnel. Le nom d’un fichier. Si spécifié, la valeur obtenue à partir de la clé de Registre est censée pour être un chemin de répertoire, et ce nom est ajouté à ce dernier. Si non spécifié, la valeur retournée à partir du Registre est censée pour être le chemin complet vers un fichier.|  
|`SearchDepth`|Optionnel. La profondeur à partir duquel rechercher des sous-dossiers pour le fichier nommé. La recherche respecte la profondeur en premier. La valeur par défaut est 0, ce qui limite la recherche sur le dossier de niveau supérieur spécifié par la valeur de la clé de Registre.|  

## <a name="remarks"></a>Remarques  
 Si les éléments sous `InstallChecks` définissent les tests à exécuter, ils ne les exécutent pas. Pour exécuter les tests, vous devez créer `Command` éléments situés sous le `Commands` élément.  

## <a name="example"></a>Exemple  
 L’exemple de code suivant montre le `InstallChecks` élément tel qu’il est utilisé dans le fichier de produit pour le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  

```xml  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  

## <a name="installconditions"></a>InstallConditions  
 Lorsque `InstallChecks` sont évaluées, il produit des propriétés. Les propriétés sont ensuite utilisées par `InstallConditions` pour déterminer si un package doit installer, ignorer ou faire échouer. Le tableau suivant répertorie les `InstallConditions`:  

|||  
|-|-|  
|`FailIf`|Le cas échéant `FailIf` condition prend la valeur true, le package échoue. Le reste des conditions ne peut pas être évalué.|  
|`BypassIf`|Le cas échéant `BypassIf` condition prend la valeur true, le package sera ignoré. Le reste des conditions ne peut pas être évalué.|  

## <a name="predefined-properties"></a>Propriétés prédéfinies  
 Le tableau suivant répertorie les `BypassIf` et `FailIf` éléments :  

|Property|Notes|Valeurs possibles|  
|--------------|-----------|---------------------|  
|`Version9X`|Numéro de version d’un système d’exploitation Windows 9 X.|4.10 = Windows 98|  
|`VersionNT`|Numéro de version d’un système d’exploitation Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professionnel SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|Numéro de version d’un système d’exploitation 64 bits Windows NT.|Comme mentionné précédemment.|  
|`VersionMsi`|Numéro de version du service Windows Installer.|2.0 = Windows Installer 2.0|  
|`AdminUser`|Spécifie si un utilisateur dispose des privilèges d’administrateur sur un système d’exploitation Windows NT.|0 ne = aucun privilège d’administrateur<br /><br /> 1 = des privilèges d’administrateur|  

 Par exemple, pour bloquer l’installation sur un ordinateur exécutant Windows 95, utilisez le code suivant :  

```xml  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  

## <a name="see-also"></a>Voir aussi  
 [\<Commandes > élément](../deployment/commands-element-bootstrapper.md)   
 [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)