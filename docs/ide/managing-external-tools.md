---
title: "Gérer les outils externes | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 38
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 66e09a22bcedb37f82eb9517a8f9d4affbe3a374
ms.openlocfilehash: ad9461bb29dba3e8e2ffe242c1f709587729ce22
ms.lasthandoff: 02/22/2017

---
# <a name="manage-external-tools"></a>Gérer les outils externes
Vous pouvez appeler des outils externes à partir de Visual Studio. Certains outils par défaut sont disponibles dans le menu **Outils**, mais vous pouvez ajouter vos propres exécutables.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Outils disponibles dans le menu Outils de Visual Studio
 Vous pouvez appeler les outils suivants à partir du menu **Outils** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également les appeler par leur nom à partir de la fenêtre **Lancement rapide**. Par exemple, pour appeler GuidGen.exe, tapez **Create GUID**.  
  
1.  Create GUID : génère un GUID.  
  
2.  Error Lookup : obtient un message d'erreur de la valeur entrée. Pour plus d’informations, consultez [Référence d’ERRLOOK](/visual-cpp/build/reference/errlook-reference).  
  
3.  ATL/MFC Trace Tool : montre des messages de trace de débogage dans les sources ATL et MFC.  
  
4.  PreEmptive Dotfuscator and Analytics : protège les programmes .NET contre l'ingénierie à rebours.  
  
5.  SPY++ : affiche les processus, threads, fenêtres, et messages de fenêtre graphiquement.  
  
6.  Éditeur de configuration de service WCF : vous permet de créer et de modifier les paramètres de configuration des services WCF.  
  
> [!WARNING]
>  Il est possible qu'une liste différente d'outils externes s'affiche, en fonction de l'édition de Visual Studio que vous avez installée et du profil de paramètres que vous avez appliqué. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="add-new-tools-to-the-tools-menu"></a>Ajouter de nouveaux outils au menu Outils 
 Vous pouvez ajouter un outil externe au menu **Outils**. Ouvrez la boîte de dialogue **Outils externes**, cliquez sur **Ajouter**, puis entrez les informations. Par exemple, l'entrée suivante peut provoquer l'ouverture de l'Explorateur Windows dans le répertoire du fichier qui est actuellement ouvert dans Visual Studio :  
  
1.  Titre : Ouvrir l'emplacement du fichier  
  
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
 [Outils de génération C/C++](/visual-cpp/build/reference/c-cpp-build-tools)

