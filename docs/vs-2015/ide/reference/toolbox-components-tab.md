---
title: Boîte à outils, onglet Composants | Documents Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 405c7db0ca437aa5462068e2be3cfcc2d76c1cae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203123"
---
# <a name="toolbox-components-tab"></a>Boîte à outils, onglet Composants
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Affiche les composants que vous pouvez ajouter aux concepteurs [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] et [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. En plus des composants [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] inclus avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], tels que les composants <xref:System.Messaging.MessageQueue> et <xref:System.Diagnostics.EventLog>, vous pouvez ajouter vos propres composants ou des composants tiers à cet onglet. Pour plus d’informations, consultez [Comment : manipuler des onglets de boîte à outils](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 Pour afficher cet onglet, dans le menu **Affichage**, sélectionnez **Boîte à outils**. Dans la **boîte à outils**, sélectionnez l’onglet **Composants**.  
  
 **BackgroundWorker**  
 Crée une instance du composant `System.ComponentModel.BackgroundWorker` qui peut exécuter une opération sur un thread dédié distinct.  
  
 **DirectoryEntry**  
 Crée une instance du composant <xref:System.DirectoryServices.DirectoryEntry> qui encapsule un nœud ou un objet dans la hiérarchie Active Directory et qui peut être utilisé pour interagir avec les fournisseurs de services Active Directory.  
  
 **DirectorySearcher**  
 Crée une instance du composant <xref:System.DirectoryServices.DirectorySearcher> que vous pouvez utiliser pour effectuer des requêtes sur Active Directory.  
  
 **ErrorProvider**  
 Crée une instance du composant `System.Windows.Forms.ErrorProvider` qui indique à l’utilisateur final qu’une erreur est associée à un contrôle sur un formulaire.  
  
 **EventLog**  
 Crée une instance du composant <xref:System.Diagnostics.EventLog> que vous pouvez utiliser pour interagir avec des journaux des événements système et personnalisés, ce qui inclut l’écriture d’événements dans un journal et la lecture de données de journal. Pour plus d’informations, consultez [Introduction au composant EventLog](http://msdn.microsoft.com/en-us/a2ba4f28-4b1a-435e-99ef-51b28e21f805).  
  
 **FileSystemWatcher**  
 Crée une instance du composant <xref:System.IO.FileSystemWatcher> que vous pouvez utiliser pour surveiller les modifications apportées à tout répertoire ou fichier auquel vous avez accès. Pour plus d’informations, consultez [Comment : configurer des instances du composant FileSystemWatcher](http://msdn.microsoft.com/en-us/2e628234-4951-4135-8a86-28b924070d50).  
  
 **HelpProvider**  
 Crée une instance du composant `System.Windows.Forms.HelpProvider` qui fournit une aide contextuelle ou en ligne pour les contrôles.  
  
 **ImageList**  
 Crée une instance du composant `System.Windows.Forms.ImageList` qui fournit des méthodes pour gérer une collection d’objets `System.Drawing.Image`.  
  
 **MessageQueue**  
 Crée une instance du composant <xref:System.Messaging.MessageQueue> que vous pouvez utiliser pour interagir avec les files d’attente de messages, notamment pour lire des messages à partir de files d’attente et écrire des messages dans ces dernières, traiter des transactions et effectuer des tâches d’administration de files d’attente. Pour plus d’informations, consultez [Utilisation de composants de messagerie](http://msdn.microsoft.com/en-us/922dbac7-26f0-4e39-b666-ccfc184793d7).  
  
 **PerformanceCounter**  
 Crée une instance du composant <xref:System.Diagnostics.PerformanceCounter> que vous pouvez utiliser pour interagir avec les compteurs de performance Windows, notamment pour créer des catégories et des instances, lire des valeurs à partir de compteurs et effectuer des calculs sur des données de compteurs. Pour plus d’informations, consultez [Analyse des seuils de performance](http://msdn.microsoft.com/en-us/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).  
  
 **Process**  
 Crée une instance du composant <xref:System.Diagnostics.Process> que vous pouvez utiliser pour arrêter, démarrer et manipuler les données associées à des processus sur votre système. Pour plus d’informations, consultez [Surveillance et gestion des processus Windows](http://msdn.microsoft.com/en-us/a86bd4c1-b92c-49a0-8f32-61d67837b45e).  
  
 **SerialPort**  
 Crée une instance du composant `System.IO.Ports.SerialPort` qui fournit les E/S synchrones et pilotées par les événements, l’accès aux états épinglés et interrompus, ainsi que l’accès aux propriétés des pilotes série.  
  
 **ServiceController**  
 Crée une instance du composant <xref:System.ServiceProcess.ServiceController> que vous pouvez utiliser pour manipuler des services existants, notamment pour démarrer et arrêter des services, ainsi que pour envoyer des commandes vers ceux-ci. Pour plus d’informations, consultez [Surveillance des services Windows](http://msdn.microsoft.com/en-us/4542ee3f-e052-4cb9-8726-58e9420de222).  
  
 **Minuterie**  
 Crée une instance du composant <xref:System.Windows.Forms.Timer> que vous pouvez utiliser pour ajouter une fonctionnalité à durée définie à vos applications Windows. Pour plus d’informations, consultez [Timer, composant](http://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).  
  
> [!NOTE]
>  Il existe également un composant <xref:System.Timers.Timer> basé sur le système que vous pouvez ajouter à la **boîte à outils**. Ce <xref:System.Timers.Timer> est optimisé pour les applications serveur. Le <xref:System.Windows.Forms.Timer> Windows Forms, quant à lui, convient mieux à une utilisation sur les Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation à l’aide de composants](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [Procédures pas à pas relatives à la programmation de composants](http://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [Boîte à outils](../../ide/reference/toolbox.md)   
 [Choisir des éléments de boîte à outils, boîte de dialogue (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)



