---
title: Paramètres de sécurité avancés, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 283428e4d4b2c81179d8dbd8ff6200c1d7140eae
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758724"
---
# <a name="advanced-security-settings-dialog-box"></a>Paramètres de sécurité avancés, boîte de dialogue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Cette boîte de dialogue vous permet de spécifier les paramètres de sécurité concernant le débogage dans la zone.  
  
 Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Sécurité**. Dans la page **Sécurité**, sélectionnez **Activer les paramètres de sécurité ClickOnce**, cliquez sur **Il s’agit d’une application de confiance partielle**, puis sur **Avancé**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Déboguer cette application à l’aide du jeu d’autorisations sélectionné**  
 Si vous cochez cette case, le jeu d’autorisations sélectionné dans la page **Sécurité** est utilisé pendant le débogage. Cette option est activée par défaut.  
  
 Pour que le débogage dans une zone de sécurité fonctionne, cette option ainsi que l’option **Activer le processus d’hébergement Visual Studio** (disponible dans la page **Déboguer** du **Concepteur de projets**) doivent être activées.  
  
 Pour les projets d’application de navigateur web WPF, l’option **Déboguer cette application à l’aide du jeu d’autorisations sélectionné** est cochée et désactivée.  
  
 **Autoriser l’application à accéder à son site d’origine**  
 Si vous cochez cette case, l’application peut accéder au site web ou au partage serveur sur lequel il est publié. Cette option est activée par défaut.  
  
 **Déboguer cette application comme si elle était téléchargée de l’URL suivante**  
 Si vous devez permettre à l’application d’accéder au site web ou au partage serveur qui correspond à **l’URL d’installation** que vous avez spécifiée dans la page **Publier**, tapez cette URL ici. Cette option est disponible uniquement quand l’option **Autoriser l’application à accéder à son site d’origine** est sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Page Sécurité, Concepteur de projet](../../ide/reference/security-page-project-designer.md)
