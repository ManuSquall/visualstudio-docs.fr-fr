---
title: Chaînes de substitution utilisées dans. Pkgdef et. Fichiers Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160534"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Chaînes de substitution utilisées dans les fichiers .Pkgdef et .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser les chaînes de substitution listées ci-dessous dans les fichiers. pkgdef et. pkgundef que vous définissez pour votre application Visual Studio isolated Shell.  
  
## <a name="substitution-strings"></a>Chaînes de substitution  
  
|Chaîne|Description|  
|------------|-----------------|  
|$=*RegistryEntry*$|Valeur de l’entrée *RegistryEntry* . Si la chaîne d’entrée de Registre se termine par une barre oblique inverse ( \\ ), la valeur par défaut de la sous-clé de Registre est utilisée. Par exemple, la chaîne de substitution $ = HKEY_CURRENT_USER \Environment\TEMP $ est développée dans le dossier temporaire de l’utilisateur actuel.|  
|$AppName $|Nom qualifié de l’application qui est passée au AppEnv.dll points d’entrée. Le nom qualifié est constitué du nom de l’application, d’un trait de soulignement et de l’identificateur de classe (CLSID) de l’objet Automation d’application, qui est également enregistré comme valeur du paramètre ThisVersionDTECLSID dans le fichier Project. pkgdef.|  
|$AppDataLocalFolder|Sous-dossier sous% LOCALAPPDATA% pour cette application.|  
|$BaseInstallDir $|Le chemin d’accès complet de l’emplacement où Visual Studio a été installé.|  
|$CommonFiles $|Valeur de la variable d’environnement% CommonProgramFiles%.|  
|$MyDocuments $|Chemin d’accès complet du dossier Mes documents de l’utilisateur actuel.|  
|$PackageFolder $|Chemin d’accès complet du répertoire qui contient les fichiers d’assembly de package pour l’application.|  
|$ProgramFiles $|Valeur de la variable d’environnement% ProgramFiles%.|  
|$RootFolder $|Chemin d’accès complet du répertoire racine de l’application.|  
|$RootKey $|Clé de Registre racine pour l’application. Par défaut, la racine se trouve dans HKEY_CURRENT_USER \Software \\ *CompanyName* \\ *ProjectName* \\ *NuméroVersion* (quand l’application est en cours d’exécution, _Config est ajouté à cette clé). Elle est définie par la valeur RegistryRoot dans le fichier *SolutionName*. pkgdef.<br /><br /> La $RootKey $ String peut être utilisée pour récupérer une valeur de Registre sous la sous-clé d’application. Par exemple, la chaîne « $ = $RootKey $ \AppIcon $ » retourne la valeur de l’entrée AppIcon sous la sous-clé racine de l’application.<br /><br /> L’analyseur traite le fichier. pkgdef de manière séquentielle et peut accéder à une entrée de Registre sous la sous-clé d’application uniquement si l’entrée a déjà été définie.|  
|$ShellFolder $|Le chemin d’accès complet de l’emplacement où Visual Studio a été installé.|  
|$System $|Dossier Windows\System32.|  
|$WINDIR $|Dossier Windows.|  
  
 Si l’analyseur ne reconnaît pas la chaîne de substitution ou s’il ne peut pas déterminer la valeur d’une entrée de registre ou d’une variable d’environnement, il n’effectue pas de substitution sur cette partie de la chaîne.
