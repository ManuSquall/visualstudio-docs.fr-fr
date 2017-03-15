---
title: "Gérer les outils externes | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
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
ms.sourcegitcommit: c36d97b83aa0892235c8f196cf6af63520b3547c
ms.openlocfilehash: a31b90643e3707348595fce02ec37a1c02a97195
ms.lasthandoff: 03/01/2017

---
# <a name="manage-external-tools"></a>Gérer les outils externes
Vous pouvez appeler des outils externes depuis Visual Studio en utilisant le menu **Outils**. Certains outils par défaut sont disponibles dans le menu **Outils**, mais vous pouvez ajouter vos propres exécutables.  

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Outils disponibles dans le menu Outils de Visual Studio
 Le menu **Outils** contient plusieurs commandes prédéfinies comme :

*  **Extensions et mises à jour** pour [gérer les extensions Visual Studio](finding-and-using-visual-studio-extensions.md)
*  **Gestionnaire des extraits de code...** pour [organiser les extraits de code](code-snippets.md#code-snippet-manager)
*  **PreEmptive Protection - Dotfuscator** pour lancer [Dotfuscator Community Edition (CE)](dotfuscator/index.md) s’il est [installé](dotfuscator/install.md)
*  **Personnaliser...** pour [personnaliser les menus et les barres d’outils](how-to-customize-menus-and-toolbars-in-visual-studio)
*  **Options...** pour [définir différentes options de l’IDE Visual Studio et d’autres outils](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Ajouter de nouveaux outils au menu Outils 
 Vous pouvez ajouter un outil externe au menu **Outils**. Ouvrez la boîte de dialogue **Outils externes...**, cliquez sur **Ajouter** puis entrez les informations. Par exemple, l'entrée suivante peut provoquer l'ouverture de l'Explorateur Windows dans le répertoire du fichier qui est actuellement ouvert dans Visual Studio :  
  
1.  Titre : *Ouvrir l’emplacement du fichier*
  
2.  Commande : `explorer.exe`  
  
3.  Arguments : `/root, "$(ItemDir)"`  
  
 Voici une liste complète des arguments qui peuvent être utilisés lors de la définition d’un outil externe.
  
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

