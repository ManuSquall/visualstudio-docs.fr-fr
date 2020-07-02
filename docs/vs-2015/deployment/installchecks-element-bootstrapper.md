---
title: '&lt;InstallChecks &gt; , élément (programme d’amorçage) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e78f3c1174d2a288a9ffc432f0206aed4956fe8f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531818"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks &gt; , élément (programme d’amorçage)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' `InstallChecks` élément prend en charge le démarrage d’un grand nombre de tests sur l’ordinateur local pour s’assurer que toutes les conditions préalables appropriées pour une application ont été installées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Cet élément est un élément enfant facultatif de `InstallChecks` . Pour chaque instance de `AssemblyCheck` , le programme d’amorçage s’assure que l’assembly identifié par l’élément existe dans le global assembly cache (GAC). Il ne contient aucun élément et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous l' `InstallConditions` élément, qui est un enfant de l' `Command` élément. Pour plus d’informations, consultez [ \<Commands> élément](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obligatoire. Nom qualifié complet de l’assembly à vérifier.|  
|`PublicKeyToken`|Obligatoire. La forme abrégée de la clé publique associée à cet assembly avec nom fort. Tous les assemblys stockés dans le GAC doivent avoir un nom, une version et une clé publique.|  
|`Version`|Obligatoire. Version de l'assembly.<br /><br /> Le numéro de version a le format \<*major version*> . \<*minor version*> . \<*build version*> . \<*revision version*> .|  
|`Language`|facultatif. Langage d’un assembly localisé. La valeur par défaut est `neutral`.|  
|`ProcessorArchitecture`|facultatif. Processeur de l’ordinateur ciblé par cette installation. La valeur par défaut est `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks` . Pour chaque instance de `ExternalCheck` , le programme d’amorçage exécute le programme externe nommé dans un processus distinct et stocke son code de sortie dans la propriété indiquée par `Property` . `ExternalCheck`est utile pour implémenter des contrôles de dépendance complexes, ou lorsque la seule façon de vérifier l’existence d’un composant consiste à l’instancier.  
  
 `ExternalCheck`ne contient aucun élément et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous l' `InstallConditions` élément, qui est un enfant de l' `Command` élément. Pour plus d’informations, consultez [ \<Commands> élément](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obligatoire. Programme externe à exécuter. Le programme doit faire partie du package de distribution du programme d’installation.|  
|`Arguments`|facultatif. Fournit des arguments de ligne de commande à l’exécutable nommé par `PackageFile` .|  
  
## <a name="filecheck"></a>FileCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks` . Pour chaque instance de `FileCheck` , le programme d’amorçage détermine si le fichier nommé existe et retourne le numéro de version du fichier. Si le fichier n’a pas de numéro de version, le programme d’amorçage définit la propriété nommée par `Property` sur 0. Si le fichier n’existe pas, `Property` n’est pas défini sur une valeur.  
  
 `FileCheck`ne contient aucun élément et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous l' `InstallConditions` élément, qui est un enfant de l' `Command` élément. Pour plus d’informations, consultez [ \<Commands> élément](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Obligatoire. Nom du fichier à rechercher.|  
|`SearchPath`|Obligatoire. Disque ou dossier dans lequel rechercher le fichier. Il doit s’agir d’un chemin d’accès relatif si `SpecialFolder` est assigné ; sinon, il doit s’agir d’un chemin d’accès absolu.|  
|`SpecialFolder`|facultatif. Un dossier qui a une signification spéciale pour Windows ou pour [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . La valeur par défaut consiste à interpréter `SearchPath` comme un chemin d’accès absolu. Les valeurs valides sont les suivantes :<br /><br /> `AppDataFolder`. Le dossier Application Data pour cette [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application ; propre à l’utilisateur actuel.<br /><br /> `CommonAppDataFolder`. Le dossier Application Data utilisé par tous les utilisateurs.<br /><br /> `CommonFilesFolder`. Dossier Fichiers communs de l’utilisateur actuel.<br /><br /> `LocalDataAppFolder`. Dossier de données pour les applications non itinérantes.<br /><br /> `ProgramFilesFolder`. Le dossier Program Files standard pour les applications 32 bits.<br /><br /> `StartUpFolder`. Dossier qui contient toutes les applications lancées au démarrage du système.<br /><br /> `SystemFolder`. Dossier qui contient les DLL système 32 bits.<br /><br /> `WindowsFolder`. Dossier qui contient l’installation du système Windows.<br /><br /> `WindowsVolume`. Lecteur ou partition qui contient l’installation du système Windows.|  
|`SearchDepth`|facultatif. Profondeur à laquelle rechercher les sous-dossiers pour le fichier nommé. La recherche est prioritaire. La valeur par défaut est 0, ce qui limite la recherche au dossier de niveau supérieur spécifié par `SpecialFolder` et **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks` . Pour chaque instance de `MsiProductCheck` , le programme d’amorçage vérifie si l’installation de Microsoft Windows Installer spécifiée s’est exécutée jusqu’à ce qu’elle soit terminée. La valeur de la propriété est définie en fonction de l’état de ce produit installé. Une valeur positive indique que le produit est installé, 0 ou-1 indique qu’il n’est pas installé. (Pour plus d’informations, consultez la fonction Windows Installer SDK MsiQueryFeatureState.) . Si Windows Installer n’est pas installé sur l’ordinateur, `Property` n’est pas défini.  
  
 `MsiProductCheck`ne contient aucun élément et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous l' `InstallConditions` élément, qui est un enfant de l' `Command` élément. Pour plus d’informations, consultez [ \<Commands> élément](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obligatoire. GUID du produit installé.|  
|`Feature`|facultatif. GUID pour une fonctionnalité spécifique de l’application installée.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks` . Pour chaque instance de `RegistryCheck` , le programme d’amorçage vérifie si la clé de Registre spécifiée existe, ou s’il a la valeur indiquée.  
  
 `RegistryCheck`ne contient aucun élément et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous l' `InstallConditions` élément, qui est un enfant de l' `Command` élément. Pour plus d’informations, consultez [ \<Commands> élément](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatoire. Nom de la clé de Registre.|  
|`Value`|facultatif. Nom de la valeur de Registre à récupérer. La valeur par défaut consiste à retourner le texte de la valeur par défaut. `Value`il doit s’agir d’une chaîne ou d’une valeur DWORD.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks` . Pour chaque instance de `RegistryFileCheck` , le programme d’amorçage récupère la version du fichier spécifié, en essayant d’abord de récupérer le chemin d’accès au fichier à partir de la clé de Registre spécifiée. Cela s’avère particulièrement utile si vous souhaitez rechercher un fichier dans un répertoire spécifié comme valeur dans le registre.  
  
 `RegistryFileCheck`ne contient aucun élément et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Nom de la propriété pour stocker le résultat. Cette propriété peut être référencée à partir d’un test sous l' `InstallConditions` élément, qui est un enfant de l' `Command` élément. Pour plus d’informations, consultez [ \<Commands> élément](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatoire. Nom de la clé de Registre. Sa valeur est interprétée comme le chemin d’accès à un fichier, à moins que l' `File` attribut ne soit défini. Si cette clé n’existe pas, `Property` n’est pas défini.|  
|`Value`|facultatif. Nom de la valeur de Registre à récupérer. La valeur par défaut consiste à retourner le texte de la valeur par défaut. `Value`doit être une chaîne.|  
|`FileName`|facultatif. Nom d’un fichier. S’il est spécifié, la valeur obtenue à partir de la clé de Registre est supposée être un chemin d’accès de répertoire, et ce nom est ajouté à celui-ci. S’il n’est pas spécifié, la valeur retournée par le Registre est supposée être le chemin d’accès complet à un fichier.|  
|`SearchDepth`|facultatif. Profondeur à laquelle rechercher les sous-dossiers pour le fichier nommé. La recherche est prioritaire. La valeur par défaut est 0, ce qui limite la recherche au dossier de niveau supérieur spécifié par la valeur de la clé de registre.|  
  
## <a name="remarks"></a>Remarques  
 Tandis que les éléments sous `InstallChecks` définissent les tests à exécuter, ils ne les exécutent pas. Pour exécuter les tests, vous devez créer des `Command` éléments sous l' `Commands` élément.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l' `InstallChecks` élément tel qu’il est utilisé dans le fichier de produit pour [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Lorsque `InstallChecks` sont évalués, ils produisent des propriétés. Les propriétés sont ensuite utilisées par `InstallConditions` pour déterminer si un package doit installer, ignorer ou échouer. Le tableau suivant répertorie les `InstallConditions` éléments suivants :  
  
|Nom|Description|
|-|-|  
|`FailIf`|Si une `FailIf` condition est évaluée sur true, le package échoue. Les autres conditions ne seront pas évaluées.|  
|`BypassIf`|Si une `BypassIf` condition a la valeur true, le package est contourné. Les autres conditions ne seront pas évaluées.|  
  
## <a name="predefined-properties"></a>Propriétés prédéfinies  
 Le tableau suivant répertorie `BypassIf` les `FailIf` éléments et :  
  
|Propriété|Notes|Valeurs possibles|  
|--------------|-----------|---------------------|  
|`Version9X`|Numéro de version d’un système d’exploitation Windows 9X.|4,10 = Windows 98|  
|`VersionNT`|Numéro de version d’un système d’exploitation basé sur Windows NT.|Major.Minor.ServicePack<br /><br /> 5,0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professionnel SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|Numéro de version d’un système d’exploitation Windows NT 64 bits.|Identique à ce qui a été mentionné précédemment.|  
|`VersionMsi`|Numéro de version du service Windows Installer.|2,0 = Windows Installer 2,0|  
|`AdminUser`|Spécifie si un utilisateur dispose de privilèges d’administrateur sur un système d’exploitation Windows NT.|0 = aucun privilège d’administrateur<br /><br /> 1 = privilèges d’administrateur|  
  
 Par exemple, pour bloquer l’installation sur un ordinateur exécutant Windows 95, utilisez un code tel que le suivant :  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<Commands>Appartient](../deployment/commands-element-bootstrapper.md)   
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)
