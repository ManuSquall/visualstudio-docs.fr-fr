---
title: Éléments communs des projets MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e36d5e50b15a5ede425715ec756f05ab8d014de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160407"
---
# <a name="common-msbuild-project-items"></a>Éléments communs des projets MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], un élément est une référence nommée à un ou plusieurs fichiers. Les éléments contiennent des métadonnées, comme des noms de fichiers, des chemins et des numéros de version. Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tous les types de projets ont plusieurs éléments en commun. Ces éléments sont définis dans le fichier microsoft.build.commontypes.xsd.  
  
## <a name="common-items"></a>Éléments communs  
 Voici une liste de tous les éléments de projet communs.  
  
### <a name="reference"></a>Référence  
 Représente une référence (managée) d'assembly dans le projet.  
  
|Item Name|Description|  
|---------------|-----------------|  
|HintPath|Chaîne facultative. Chemin d'accès relatif ou absolu de l'assembly.|  
|Nom|Chaîne facultative. Nom complet de l'assembly, par exemple, « System.Windows.Forms ».|  
|FusionName|Chaîne facultative. Spécifie le nom de fusion simple ou fort de l'élément.<br /><br /> La présence de cet attribut peut faire gagner du temps, car il vous évite d'ouvrir le fichier d'assembly pour obtenir le nom de fusion.|  
|SpecificVersion|Valeur booléenne facultative. Indique si seule la version figurant dans le nom de fusion doit être référencée.|  
|Alias|Chaîne facultative. Alias éventuels de la référence.|  
|Privées|Valeur booléenne facultative. Indique si la référence doit être copiée dans le dossier de sortie. Cet attribut correspond à la propriété **Copie locale** de la référence qui se trouve dans l’IDE Visual Studio.|  
  
### <a name="comreference"></a>COMReference  
 Représente une référence de composant (non managé) COM dans le projet.  
  
|Item Name|Description|  
|---------------|-----------------|  
|Nom|Chaîne facultative. Nom complet du composant.|  
|Guid|Chaîne facultative. GUID du composant sous la forme {12345678-1234-1234-1234-1234567891234}.|  
|VersionMajor|Chaîne facultative. Partie principale du numéro de version du composant. Par exemple, « 5 » si le numéro de version complet est « 5.46 ».|  
|VersionMinor|Chaîne facultative. Partie secondaire du numéro de version du composant. Par exemple, « 46 » si le numéro de version complet est « 5.46 ».|  
|LCID|Chaîne facultative. LocaleID du composant.|  
|WrapperTool|Chaîne facultative. Nom de l'outil wrapper utilisé sur le composant, par exemple, « tlbimp ».|  
|Isolé|Valeur booléenne facultative. Indique si le composant est un composant sans inscription.|  
  
### <a name="comfilereference"></a>COMFileReference  
 Représente une liste de bibliothèques de types qui alimente la cible ResolvedComreference.  
  
|Item Name|Description|  
|---------------|-----------------|  
|WrapperTool|Chaîne facultative. Nom de l'outil wrapper utilisé sur le composant, par exemple, « tlbimp ».|  
  
### <a name="nativereference"></a>NativeReference  
 Représente un fichier manifeste natif ou une référence à un fichier de ce type.  
  
|Item Name|Description|  
|---------------|-----------------|  
|Nom|Chaîne obligatoire. Nom de base du fichier manifeste.|  
|HintPath|Chaîne obligatoire. Chemin d'accès relatif du fichier manifeste.|  
  
### <a name="projectreference"></a>ProjectReference  
 Représente une référence à un autre projet.  
  
|Item Name|Description|  
|---------------|-----------------|  
|Nom|Chaîne facultative. Nom complet de la référence.|  
|Project|Chaîne facultative. GUID de la référence sous la forme {12345678-1234-1234-1234-1234567891234}.|  
|Package|Chaîne facultative. Chemin d'accès du fichier projet référencé.|  
  
### <a name="compile"></a>Compiler  
 Représente les fichiers sources du compilateur.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte.|  
|AutoGen|Valeur booléenne facultative. Indique si le fichier a été généré pour le projet par l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|Lien|Chaîne facultative. Chemin d’accès codifiable à afficher quand le fichier se trouve physiquement en dehors de l’influence du fichier projet.|  
|Visible|Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Représente les ressources à incorporer dans l'assembly généré.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte.|  
|Générateur|Chaîne obligatoire. Nom du générateur de fichier exécuté sur cet élément.|  
|LastGenOutput|Chaîne obligatoire. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément.|  
|CustomToolNamespace|Chaîne obligatoire. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code.|  
|Lien|Chaîne facultative. Le chemin d’accès codifiable s’affiche si le fichier se trouve physiquement en dehors de l’influence du projet.|  
|Visible|Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest|  
|LogicalName|Chaîne obligatoire. Nom logique de la ressource incorporée.|  
  
### <a name="content"></a>Content  
 Représente les fichiers qui ne sont pas compilés dans le projet, mais qui peuvent être incorporés ou publiés en même temps.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte.|  
|Générateur|Chaîne obligatoire. Nom du générateur de fichier qui s'exécute sur cet élément.|  
|LastGenOutput|Chaîne obligatoire. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément.|  
|CustomToolNamespace|Chaîne obligatoire. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code.|  
|Lien|Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|PublishState|Chaîne obligatoire. État de publication du contenu, à savoir :<br /><br /> -   Default<br />-   Included<br />-   Excluded<br />-   DataFile<br />-   Prerequisite|  
|IsAssembly|Valeur booléenne facultative. Indique si le fichier est un assembly.|  
|Visible|Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest|  
  
### <a name="none"></a>None  
 Représente les fichiers qui ne doivent avoir aucun rôle dans le processus de génération.  
  
|Item Name|Description|  
|---------------|-----------------|  
|DependentUpon|Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte.|  
|Générateur|Chaîne obligatoire. Nom du générateur de fichier exécuté sur cet élément.|  
|LastGenOutput|Chaîne obligatoire. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément.|  
|CustomToolNamespace|Chaîne obligatoire. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code.|  
|Lien|Chaîne facultative. Chemin d'accès codifiable à afficher si le fichier se trouve physiquement en dehors de l'influence du projet.|  
|Visible|Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Représente le manifeste d'application de base de la build et contient les informations de sécurité de déploiement de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
### <a name="codeanalysisimport"></a>CodeAnalysisImport  
 Représente le projet FxCop à importer.  
  
### <a name="import"></a>Importer  
 Représente les assemblys dont les espaces de noms doivent être importés par le compilateur [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes des projets MSBuild](../msbuild/common-msbuild-project-properties.md)
