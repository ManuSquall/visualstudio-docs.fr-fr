---
title: "&lt;InstallChecks&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<InstallChecks> (élément du programme d'amorçage)"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# &lt;InstallChecks&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément `InstallChecks` prend en charge le lancement sur l'ordinateur local de divers tests permettant de vérifier que tous les composants requis appropriés pour une application ont été installés.  
  
## Syntaxe  
  
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
  
## AssemblyCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`.  Pour chaque instance de `AssemblyCheck`, le programme d'amorçage vérifie que l'assembly identifié par l'élément existe dans le Global Assembly Cache \(GAC\).  Il ne contient pas d'éléments et possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété pour stocker le résultat.  Cette propriété peut être référencée à partir d'un test sous l'élément `InstallConditions`, qui est un enfant de l'élément `Command`.  Pour plus d'informations, consultez [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obligatoire.  Nom complet de l'assembly à vérifier.|  
|`PublicKeyToken`|Obligatoire.  Forme abrégée de la clé publique associée à cet assembly avec nom fort.  Tous les assemblys stockés dans le GAC doivent avoir un nom, une version et une clé publique.|  
|`Version`|Obligatoire.  Version de l'assembly.<br /><br /> Le numéro de version a le format \<*version principale*\>. \<*version secondaire*\>. \<*version de build*\>. \<*version de révision*\>.|  
|`Language`|Facultatif.  Langue d'un assembly localisé.  La valeur par défaut est `neutral`.|  
|`ProcessorArchitecture`|Facultatif.  Processeur informatique ciblé par cette installation.  La valeur par défaut est `msil`.|  
  
## ExternalCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`.  Pour chaque instance de `ExternalCheck`, le programme d'amorçage exécutera le programme externe nommé dans un processus séparé et stocke son code de sortie dans la propriété indiquée par `Property`.  `ExternalCheck` est utile pour l'implémentation de contrôles de dépendance complexes, ou lorsque la seule méthode de contrôle de l'existence d'un composant consiste à l'instancier.  
  
 `ExternalCheck` ne contient pas d'éléments et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété pour stocker le résultat.  Cette propriété peut être référencée à partir d'un test sous l'élément `InstallConditions`, qui est un enfant de l'élément `Command`.  Pour plus d'informations, consultez [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obligatoire.  Programme externe à exécuter.  Le programme doit faire partie du package de distribution de l'installation.|  
|`Arguments`|Facultatif.  Fournit des arguments de ligne de commande à l'exécutable nommé par `PackageFile`.|  
  
## FileCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`.  Pour chaque instance de `FileCheck`, le programme d'amorçage détermine si le fichier nommé existe et retourne le numéro de version du fichier.  Si le fichier n'a pas de numéro de version, le programme d'amorçage définit la propriété nommée par `Property` à 0.  Si le fichier n'existe pas, `Property` n'a pas de valeur.  
  
 `FileCheck` ne contient pas d'éléments et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété pour stocker le résultat.  Cette propriété peut être référencée à partir d'un test sous l'élément `InstallConditions`, qui est un enfant de l'élément `Command`.  Pour plus d'informations, consultez [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Obligatoire.  Nom du fichier à rechercher.|  
|`SearchPath`|Obligatoire.  Disque ou dossier dans lequel rechercher le fichier.  Il doit s'agir d'un chemin d'accès relatif si `SpecialFolder` est assigné ; sinon ce chemin doit être un chemin d'accès absolu.|  
|`SpecialFolder`|Facultatif.  Dossier qui a une signification spéciale pour Windows ou [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Par défaut, `SearchPath` est interprété comme un chemin d'accès absolu.  Les valeurs valides incluent les suivantes :<br /><br /> `AppDataFolder`.  Dossier Application Data de cette application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], spécifique à l'utilisateur actuel.<br /><br /> `CommonAppDataFolder`.  Dossier Application Data utilisé par tous les utilisateurs.<br /><br /> `CommonFilesFolder`.  Dossier Fichiers communs de l'utilisateur actuel.<br /><br /> `LocalDataAppFolder`.  Dossier de données pour des applications non itinérantes.<br /><br /> `ProgramFilesFolder`.  Dossier Program Files standard pour les applications 32 bits.<br /><br /> `StartUpFolder`.  Dossier qui contient toutes les applications lancées au démarrage du système.<br /><br /> `SystemFolder`.  Dossier qui contient des DLL de système 32 bits.<br /><br /> `WindowsFolder`.  Dossier qui contient l'installation du système Windows.<br /><br /> `WindowsVolume`.  Lecteur ou partition qui contient l'installation du système Windows.|  
|`SearchDepth`|Facultatif.  Profondeur de la recherche du fichier nommé dans les sous\-dossiers.  Il s'agit d'une recherche en profondeur.  La valeur par défaut, 0, limite la recherche au dossier à la racine spécifié par `SpecialFolder` et **SearchPath**.|  
  
## MsiProductCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`.  Pour chaque instance de `MsiProductCheck`, le programme d'amorçage vérifie si l'installation Microsoft Windows Installer spécifiée s'est terminée correctement.  La valeur de propriété est définie selon l'état du produit installé.  Une valeur positive indique que le produit est installé ; la valeur 0 ou \-1 indique qu'il n'est pas installé.  \(Pour plus d'informations, reportez\-vous à la fonction MsiQueryFeatureState du Kit de développement Windows Installer.\) .  Si Windows Installer n'est pas installé sur l'ordinateur, `Property` n'est pas défini.  
  
 `MsiProductCheck` ne contient pas d'éléments et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété pour stocker le résultat.  Cette propriété peut être référencée à partir d'un test sous l'élément `InstallConditions`, qui est un enfant de l'élément `Command`.  Pour plus d'informations, consultez [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obligatoire.  GUID du produit installé.|  
|`Feature`|Facultatif.  GUID d'une fonctionnalité spécifique de l'application installée.|  
  
## RegistryCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`.  Pour chaque instance de `RegistryCheck`, le programme d'amorçage vérifie si la clé de Registre spécifiée existe, ou si elle a la valeur indiquée.  
  
 `RegistryCheck` ne contient pas d'éléments et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété pour stocker le résultat.  Cette propriété peut être référencée à partir d'un test sous l'élément `InstallConditions`, qui est un enfant de l'élément `Command`.  Pour plus d'informations, consultez [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatoire.  Nom de la clé de Registre.|  
|`Value`|Facultatif.  Nom de la clé de Registre à récupérer.  La valeur par défaut est de retourner le texte de la valeur par défaut.  `Value` doit être une Chaîne ou une valeur DWORD.|  
  
## RegistryFileCheck  
 Cet élément est un élément enfant facultatif de `InstallChecks`.  Pour chaque instance de `RegistryFileCheck`, le programme d'amorçage extrait la version du fichier spécifié, en essayant d'abord de récupérer le chemin d'accès au fichier à partir de la clé de Registre spécifiée.  Ceci est particulièrement utile si vous souhaitez rechercher un fichier dans un répertoire spécifié comme une valeur dans le Registre.  
  
 `RegistryFileCheck` ne contient pas d'éléments et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété pour stocker le résultat.  Cette propriété peut être référencée à partir d'un test sous l'élément `InstallConditions`, qui est un enfant de l'élément `Command`.  Pour plus d'informations, consultez [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatoire.  Nom de la clé de Registre.  Sa valeur est interprétée comme le chemin d'accès à un fichier, à moins que l'attribut `File` soit défini.  Si la clé n'existe pas, `Property` n'est pas défini.|  
|`Value`|Facultatif.  Nom de la clé de Registre à récupérer.  La valeur par défaut est de retourner le texte de la valeur par défaut.  `Value` doit être une Chaîne.|  
|`FileName`|Facultatif.  Nom d'un fichier.  S'il est spécifié, la valeur obtenue de la clé de Registre est supposée être un chemin d'accès au répertoire et ce nom lui est ajouté.  S'il ne l'est pas, la valeur retournée par le Registre est supposée représenter le chemin d'accès complet à un fichier.|  
|`SearchDepth`|Facultatif.  Profondeur de la recherche du fichier nommé dans les sous\-dossiers.  Il s'agit d'une recherche en profondeur.  La valeur par défaut, 0, limite la recherche au dossier à la racine spécifié par la valeur de la clé de Registre.|  
  
## Notes  
 Si les éléments sous `InstallChecks` définissent les tests à exécuter, en revanche, ils ne les exécutent pas.  Pour exécuter les tests, vous devez créer des éléments `Command` sous l'élément `Commands`.  
  
## Exemple  
 L'exemple de code suivant illustre l'utilisation de l'élément `InstallChecks` dans le fichier produit du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 Lorsque l'élément `InstallChecks` est évalué, il produit des propriétés.  Elles sont ensuite utilisées par `InstallConditions` pour déterminer si un package doit être installé, ignoré ou en échec.  Le tableau suivant décrit `InstallConditions` :  
  
|||  
|-|-|  
|`FailIf`|Si une condition `FailIf` prend la valeur True, le package échouera.  Le reste des conditions ne sera pas évalué.|  
|`BypassIf`|Si une condition `BypassIf` prend la valeur True, le package sera ignoré.  Le reste des conditions ne sera pas évalué.|  
  
## Propriétés prédéfinies  
 Le tableau suivant répertorie les éléments `FailIf` et `BypassIf` :  
  
|Propriété|Remarques|Valeurs possibles|  
|---------------|---------------|-----------------------|  
|`Version9X`|Numéro de version d'un système d'exploitation Windows 9X.|4.10 \= Windows 98|  
|`VersionNT`|Numéro de version d'un système d'exploitation basé sur Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 \= Windows 2000<br /><br /> 5.1.0 \= Windows XP<br /><br /> 5.1.2 \= Windows XP Professionnel SP2<br /><br /> 5.2.0 \= Windows Server 2003|  
|`VersionNT64`|Numéro de version d'un système d'exploitation basé sur Windows NT 64 bits.|Comme mentionné précédemment.|  
|`VersionMsi`|Numéro de version du service Windows Installer.|2.0 \= Windows Installer 2.0|  
|`AdminUser`|Spécifie si un utilisateur a des privilèges d'administrateur sur un système d'exploitation basé sur Windows NT.|0 \= aucun privilège d'administrateur<br /><br /> 1 \= privilèges d'administrateur|  
  
 Par exemple, pour bloquer l'installation sur un ordinateur exécutant Windows 95, utilisez un code semblable au suivant :  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## Voir aussi  
 [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md)   
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)