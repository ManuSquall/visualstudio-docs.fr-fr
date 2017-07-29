---
title: "Paramètres internationaux, Environnement, boîte de dialogue Options | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: b92985ecd674fe750504c3aa85634b8c09fcdd5a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="international-settings-environment-options-dialog-box"></a>Paramètres internationaux, Environnement, boîte de dialogue Options
La page Paramètres internationaux vous permet de changer la langue par défaut quand vous avez plusieurs versions linguistiques de l'environnement de développement intégré (IDE) installé sur votre ordinateur. Vous pouvez accéder à cette boîte de dialogue en sélectionnant **Options** dans le menu **Outils**, puis en choisissant **Paramètres internationaux** dans le dossier **Environnement**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.  
  
> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **Langue**  
 Répertorie les langues disponibles pour les versions linguistiques du produit installé. Cette option n'est disponible que si vous avez plusieurs versions linguistiques installées sur votre ordinateur. Si plusieurs versions linguistiques de produits ou si une installation mixte de versions linguistiques de produits partagent le même environnement, la langue sélectionnée est changée en **Identique à Microsoft Windows**.  
  
> [!CAUTION]
>  Dans un système où plusieurs langues sont installées, les outils de génération Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe et les fichiers associés) ne sont pas affectés par ce paramètre. Ces outils utilisent la version pour la dernière langue installée, et les outils pour la langue précédemment installée sont remplacés, car les outils de génération Visual C++ n'utilisent pas le modèle de DLL satellite.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer des modules linguistiques](../../install/install-visual-studio.md#install-language-packs)   
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)
