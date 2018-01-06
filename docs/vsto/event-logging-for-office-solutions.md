---
title: "Journalisation des événements pour les Solutions Office | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 55864eda9d62be5988d1d3ab7262c4d34c0662f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="event-logging-for-office-solutions"></a>Journalisation des événements pour les solutions Office
  Vous pouvez utiliser l’observateur d’événements de Windows pour consulter les messages d’exception capturés par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] lors de l’installation ou de la désinstallation de solutions Office. Vous pouvez utiliser ces messages du journal des événements pour résoudre les problèmes d’installation et de déploiement.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="reading-the-event-log"></a>Lecture du journal des événements  
 Ouvrez l’ **Observateur d’événements** et filtrez les événements que vous souhaitez afficher.  
  
#### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Pour lire le journal des événements dans Windows Server 2003 et Windows XP  
  
1.  Dans le Panneau de configuration, ouvrez **Outils d’administration**.  
  
2.  Démarrez l’ **Observateur d’événements**.  
  
3.  Dans la liste des journaux des événements, sélectionnez **Application**.  
  
4.  Dans le menu **Affichage** , cliquez sur **Filtrer**.  
  
5.  Dans la liste **Source d’événement** , sélectionnez **VSTO 4.0**.  
  
6.  Pour les événements d’installation, dans la zone **ID d’événement** , tapez **4096**.  
  
7.  Cliquez sur **OK** pour afficher la vue filtrée.  
  
#### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Pour lire le journal des événements dans Windows 7, Windows Vista et Windows Server 2008  
  
1.  Dans le Panneau de configuration, ouvrez **Outils d’administration**.  
  
2.  Démarrez l’ **Observateur d’événements**.  
  
3.  Développez **Journaux Windows**.  
  
4.  Dans la liste des journaux des événements, sélectionnez **Application**.  
  
5.  Dans le menu **Action** , cliquez sur **Filtrer le journal actuel**.  
  
6.  Dans la liste **Source d’événement** , sélectionnez **VSTO 4.0**.  
  
7.  Pour les événements d’installation, dans la zone **ID d’événement** , tapez **4096**.  
  
8.  Cliquez sur **OK** pour afficher la vue filtrée.  
  
 L’observateur d’événements fournit les informations suivantes :  
  
-   L’emplacement du manifeste de déploiement pour la solution.  
  
-   Un message qui décrit la cause de l’erreur ou de l’exception.  
  
 Ces messages d’exception peuvent vous aider à déterminer la cause d’un problème d’installation, tel qu’un certificat non approuvé, un emplacement de document non approuvé ou un manifeste de déploiement non valide.  
  
 Après la désinstallation d’une solution Office, les messages d’exception restent dans le journal des événements.  
  
 Pour afficher ou enregistrer les messages d’exception lors de l’exécution d’une solution Office, consultez [le débogage des projets Office](../vsto/debugging-office-projects.md) et [le débogage des projets Office](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Localisation  
 La langue du message d’exception est déterminée par la langue du runtime de Visual Studio Tools pour Office. Par exemple, si le module linguistique japonais est installé sur l’ordinateur de l’utilisateur final, le message d’exception est écrit dans le journal des événements en japonais.  
  
## <a name="disabling-the-event-logger"></a>Désactivation du journal des événements  
 Par défaut, le journal des événements est activé lorsque vous installez ou désinstallez des solutions Office. Vous pouvez désactiver le journal des événements en affectant la valeur « 1 » (un) à la variable d’environnement VSTO_EVENTLOGDISABLED.  
  
#### <a name="to-disable-the-event-log"></a>Pour désactiver le journal des événements  
  
1.  Dans le Panneau de configuration, ouvrez **Système**.  
  
2.  Sous l'onglet **Avancé** , cliquez sur **Variables d'environnement**.  
  
3.  Dans le volet **Variables système** , cliquez sur **Nouveau**.  
  
4.  Dans la boîte de dialogue **Nouvelle variable système** , tapez **VSTO_EVENTLOGDISABLED** dans la zone **Nom de la variable** .  
  
5.  Dans la zone **Valeur de la variable** , tapez **1**.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Dépannage du déploiement de solutions Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  