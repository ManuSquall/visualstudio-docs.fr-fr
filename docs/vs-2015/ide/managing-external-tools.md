---
title: Gestion des outils externes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a59432d6b630606ac5c133e8a5811186fcf7c34
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58866758"
---
# <a name="managing-external-tools"></a>Gestion des outils externes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez appeler des outils externes à partir de Visual Studio. Certains outils par défaut sont disponibles dans le menu **Outils**, mais vous pouvez ajouter vos propres exécutables.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Outils disponibles dans le menu Outils de Visual Studio  
 Vous pouvez appeler les outils suivants à partir du menu **Outils** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous pouvez également les appeler par leur nom à partir de la fenêtre **Lancement rapide**. Par exemple, pour appeler GuidGen.exe, tapez **Create GUID**.  
  
1.  Create GUID : génère un GUID.  
  
2.  Error Lookup : obtient un message d'erreur de la valeur entrée. Pour plus d’informations, consultez [Référence d’ERRLOOK](http://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).  
  
3.  ATL/MFC Trace Tool : montre des messages de trace de débogage dans les sources ATL et MFC.  
  
4.  PreEmptive Protection - Dotfuscator : Protège les programmes .NET contre l’ingénierie à rebours.  
  
5.  SPY ++ : Affiche les processus, threads, windows et messages de fenêtre graphiquement.  
  
6.  Éditeur de Configuration de Service WCF : Vous permet de créer et modifier les paramètres de configuration pour les services WCF.  
  
> [!WARNING]
>  Il est possible qu'une liste différente d'outils externes s'affiche, en fonction de l'édition de Visual Studio que vous avez installée et du profil de paramètres que vous avez appliqué. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="adding-new-tools"></a>Ajout de nouveaux outils  
 Vous pouvez ajouter un outil externe au menu **Outils**. Ouvrez la boîte de dialogue **Outils externes**, cliquez sur **Ajouter**, puis entrez les informations. Par exemple, l'entrée suivante peut provoquer l'ouverture de l'Explorateur Windows dans le répertoire du fichier qui est actuellement ouvert dans Visual Studio :  
  
1.  Titre : Emplacement du fichier ouvert  
  
2.  Commande : explorer.exe  
  
3.  Arguments : /root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Arguments des outils externes  
 Les arguments suivants sont des variables Visual Studio assignées lorsque vous exécutez un outil externe. Des liens vers des outils externes (par exemple, Bloc-notes ou Spy++) peuvent être répertoriés dans le menu **Outils** à l’aide de la boîte de dialogue Outils externes.  
  
> [!NOTE]
>  La barre d'état IDE affiche les variables Ligne active et Colonne active pour indiquer l'emplacement du point d'insertion dans l'éditeur de code actif. La variable Texte actif retourne le texte ou le code sélectionné à cet emplacement.  
  
|Nom|Argument|Description|  
|----------|--------------|-----------------|  
|Chemin d'accès de l'élément|$(ItemPath)|Nom complet du fichier actif (lecteur + chemin d'accès + nom de fichier).|  
|Répertoire de l'élément|$(ItemDir)|Répertoire du fichier actif (lecteur + chemin d'accès).|  
|Nom de fichier de l'élément|$(ItemFilename)|Nom du fichier actif (nom de fichier).|  
|Extension de l'élément|$(ItemExt)|Extension du nom du fichier actif.|  
|Ligne active|$(CurLine)|Position de la ligne active du curseur dans la fenêtre de code.|  
|Colonne active.|$(CurCol)|Position de la colonne active du curseur dans la fenêtre de code.|  
|Texte actif|$(CurText)|Texte sélectionné.|  
|Chemin d'accès cible|$(TargetPath)|Nom de fichier complet de l'élément à générer (lecteur + chemin d'accès + nom de fichier).|  
|Répertoire cible|$(TargetDir)|Répertoire de l'élément à générer.|  
|Nom cible|$(TargetName)|Nom de fichier de l'élément à générer.|  
|Extension cible|$(TargetExt)|Extension de nom de fichier de l'élément à générer.|  
|Répertoire binaire|$(BinDir)|Emplacement final du binaire en cours de génération (sous la forme lecteur + chemin d’accès). Par exemple :**\\...\Mes documents\Visual Studio \<Version>\\<NomProjet\>\bin\debug**|  
|Répertoire du projet|$(ProjDir)|Répertoire du projet actif (lecteur + chemin d'accès).|  
|Nom du fichier projet|$(ProjFileName)|Nom de fichier du projet actif (lecteur + chemin d'accès + nom de fichier).|  
|Répertoire de la solution|$(SolutionDir)|Répertoire de la solution active (lecteur + chemin d'accès).|  
|Nom du fichier solution|$(SolutionFileName)|Nom de fichier de la solution active (lecteur + chemin d’accès + nom de fichier).|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de génération C/C++](http://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
