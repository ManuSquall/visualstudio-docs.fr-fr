---
title: Boîte à outils, onglet Composants | Documents Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661566"
---
# <a name="toolbox-components-tab"></a>Boîte à outils, onglet Composants
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Affiche les composants que vous pouvez ajouter aux concepteurs [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] et [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. En plus des [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] composants inclus avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , tels que les <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> composants et, vous pouvez ajouter vos propres composants ou des composants tiers à cet onglet. Pour plus d’informations, consultez [Comment : manipuler les onglets de la boîte à outils](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Pour afficher cet onglet, dans le menu **Affichage**, sélectionnez **Boîte à outils**. Dans la **boîte à outils**, sélectionnez l’onglet **Composants**.

 **BackgroundWorker** Crée une `System.ComponentModel.BackgroundWorker` instance de composant qui peut exécuter une opération sur un thread séparé et dédié.

 **DirectoryEntry** Crée une <xref:System.DirectoryServices.DirectoryEntry> instance de composant qui encapsule un nœud ou un objet dans la hiérarchie Active Directory et qui peut être utilisé pour interagir avec les fournisseurs de services Active Directory.

 **DirectorySearcher** Crée une <xref:System.DirectoryServices.DirectorySearcher> instance de composant que vous pouvez utiliser pour exécuter des requêtes sur les Active Directory.

 **ErrorProvider** Crée une `System.Windows.Forms.ErrorProvider` instance de composant, qui indique à l’utilisateur final qu’une erreur est associée à un contrôle sur un formulaire.

 **Journal des événements** Crée une <xref:System.Diagnostics.EventLog> instance de composant que vous pouvez utiliser pour interagir avec les journaux des événements système et personnalisés, y compris l’écriture d’événements dans un journal et la lecture de données de journal. Pour plus d’informations, consultez [Introduction au composant EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Crée une <xref:System.IO.FileSystemWatcher> instance de composant que vous pouvez utiliser pour surveiller les modifications apportées à tout répertoire ou fichier auquel vous avez accès. Pour plus d’informations, consultez [Comment : configurer des instances du composant FileSystemWatcher](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider** Crée une `System.Windows.Forms.HelpProvider` instance de composant qui fournit l’aide contextuelle ou en ligne pour les contrôles.

 **ImageList** Crée une `System.Windows.Forms.ImageList` instance de composant qui fournit des méthodes pour gérer une collection d' `System.Drawing.Image` objets.

 **MessageQueue** Crée une <xref:System.Messaging.MessageQueue> instance de composant que vous pouvez utiliser pour interagir avec les files d’attente de messages, notamment pour lire et écrire des messages dans des files d’attente, traiter des transactions et effectuer des tâches d’administration de file d’attente. Pour plus d’informations, consultez [Utilisation de composants de messagerie](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Crée une <xref:System.Diagnostics.PerformanceCounter> instance de composant que vous pouvez utiliser pour interagir avec les compteurs de performance Windows, notamment pour créer des catégories et des instances, lire des valeurs à partir de compteurs et effectuer des calculs sur des données de compteur. Pour plus d’informations, consultez [Analyse des seuils de performance](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Processus** Crée une <xref:System.Diagnostics.Process> instance de composant que vous pouvez utiliser pour arrêter, démarrer et manipuler les données associées aux processus sur votre système. Pour plus d’informations, consultez [Surveillance et gestion des processus Windows](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **SerialPort** Crée une `System.IO.Ports.SerialPort` instance de composant qui fournit des e/s synchrones et pilotées par les événements, l’accès aux États d’épinglage et d’arrêt, et l’accès aux propriétés de pilote série.

 **ServiceController** Crée une <xref:System.ServiceProcess.ServiceController> instance de composant que vous pouvez utiliser pour manipuler des services existants, notamment pour démarrer et arrêter des services et envoyer des commandes à ceux-ci. Pour plus d’informations, consultez [Surveillance des services Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Minuteur** Crée une <xref:System.Windows.Forms.Timer> instance de composant que vous pouvez utiliser pour ajouter une fonctionnalité basée sur le temps à vos applications Windows. Pour plus d’informations, consultez [Timer, composant](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> Il existe également un composant <xref:System.Timers.Timer> basé sur le système que vous pouvez ajouter à la **boîte à outils**. Ce <xref:System.Timers.Timer> est optimisé pour les applications serveur. Le <xref:System.Windows.Forms.Timer> Windows Forms, quant à lui, convient mieux à une utilisation sur les Windows Forms.

## <a name="see-also"></a>Voir aussi
 [Programmation à l’aide de composants composant de](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [programmation procédures pas à pas](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) boîte [à outils](../../ide/reference/toolbox.md) [choisir des éléments de boîte à outils (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
