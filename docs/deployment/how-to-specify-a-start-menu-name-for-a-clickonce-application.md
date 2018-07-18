---
title: 'Comment : spécifier un nom de Menu Démarrer pour une Application ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a089fa67c975496c56d29d2d55c2f055888c96d9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558865"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Comment : spécifier un nom de menu Démarrer pour une application ClickOnce
Lorsqu’un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est installée pour une utilisation en ligne et hors connexion, une entrée est ajoutée à la **Démarrer** menu et le **Ajout / Suppression de programmes** liste. Par défaut, le nom complet est le même que le nom de l’assembly d’application, mais vous pouvez modifier le nom complet en définissant **nom de produit** dans les **Options de publication** boîte de dialogue.  
  
 **Nom de produit** s’affichera sur la page publish.htm ; pour une application hors ligne installée, il sera le nom de l’entrée dans le **Démarrer** menu et il sera également le nom qui apparaît dans **ajouter ou supprimer Programmes**.  
  
 **Nom de l’éditeur** s’affiche dans la page publish.htm ci-dessus **nom de produit**, et pour une application hors ligne installée, il sera également le nom du dossier qui contient l’icône de l’application dans le **Démarrer**  menu.  
  
 Vous pouvez définir le **nom de produit** et **nom de l’éditeur** propriétés dans le **Options de publication** boîte de dialogue, disponible sur le **publier** page de la **Concepteur de projets**.  
  
### <a name="to-specify-a-start-menu-name"></a>Pour spécifier un nom de menu Démarrer  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **Options** bouton pour ouvrir la **Options de publication** boîte de dialogue.  
  
4.  Cliquez sur **Description**.  
  
5.  Dans le **Options de publication** boîte de dialogue, entrez le nom à afficher dans la zone **nom de produit**.  
  
6.  Si vous le souhaitez, vous pouvez entrer un nom de serveur de publication dans **nom de l’éditeur**.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)