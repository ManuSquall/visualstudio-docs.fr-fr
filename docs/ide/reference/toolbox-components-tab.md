---
title: Boîte à outils, onglet Composants
description: En savoir plus sur les composants que vous trouverez dans l’onglet composants de la fenêtre boîte à outils.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40ba84712a343a071d6213dc9cd985727fc20ebf
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560939"
---
# <a name="toolbox-components-tab"></a>Boîte à outils, onglet Composants

Affiche les composants que vous pouvez ajouter aux concepteurs Visual Basic et C# pour Windows Forms. En plus des composants .NET inclus avec Visual Studio, comme les composants <xref:System.Messaging.MessageQueue> et <xref:System.Diagnostics.EventLog>, vous pouvez ajouter vos propres composants ou des composants de tiers à cet onglet.

Pour afficher cet onglet, ouvrez un concepteur Windows Forms. Sélectionnez **Afficher** la  >  **boîte à outils**. Dans **Boîte à outils**, sélectionnez l’onglet **Composants**.

## <a name="components"></a>Composants

**BackgroundWorker**

Crée une instance du composant <xref:System.ComponentModel.BackgroundWorker> qui peut exécuter une opération sur un thread dédié distinct. Pour plus d’informations, consultez [BackgroundWorker, composant](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Crée une instance du composant <xref:System.DirectoryServices.DirectoryEntry> qui encapsule un nœud ou un objet dans la hiérarchie Active Directory et qui peut être utilisé pour interagir avec les fournisseurs de services Active Directory.

**DirectorySearcher**

Crée une instance du composant <xref:System.DirectoryServices.DirectorySearcher> que vous pouvez utiliser pour effectuer des requêtes sur Active Directory.

**ErrorProvider**

Crée une instance du composant <xref:System.Windows.Forms.ErrorProvider> qui indique à l’utilisateur final qu’une erreur est associée à un contrôle sur un formulaire. Pour plus d’informations, consultez [ErrorProvider, composant](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Crée une instance du composant <xref:System.Diagnostics.EventLog> que vous pouvez utiliser pour interagir avec des journaux des événements système et personnalisés, ce qui inclut l’écriture d’événements dans un journal et la lecture de données de journal.

**FileSystemWatcher**

Crée une instance du composant <xref:System.IO.FileSystemWatcher> que vous pouvez utiliser pour surveiller les modifications apportées à tout répertoire ou fichier auquel vous avez accès.

**HelpProvider**

Crée une instance du composant <xref:System.Windows.Forms.HelpProvider> qui fournit une aide contextuelle ou en ligne pour les contrôles. Pour plus d’informations, consultez [HelpProvider, composant](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Crée une instance du composant <xref:System.Windows.Forms.ImageList> qui fournit des méthodes pour gérer une collection d’objets <xref:System.Drawing.Image>. Pour plus d’informations, consultez [ImageList, composant](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Crée une instance du composant <xref:System.Messaging.MessageQueue> que vous pouvez utiliser pour interagir avec les files d’attente de messages, notamment pour lire des messages à partir de files d’attente et écrire des messages dans ces dernières, traiter des transactions et effectuer des tâches d’administration de files d’attente.

**PerformanceCounter**

Crée une instance du composant <xref:System.Diagnostics.PerformanceCounter> que vous pouvez utiliser pour interagir avec les compteurs de performance Windows, notamment pour créer des catégories et des instances, lire des valeurs à partir de compteurs et effectuer des calculs sur des données de compteurs.

**Processus**

Crée une instance du composant <xref:System.Diagnostics.Process> que vous pouvez utiliser pour arrêter, démarrer et manipuler les données associées à des processus sur votre système.

**SerialPort**

Crée une instance du composant <xref:System.IO.Ports.SerialPort> qui fournit les E/S synchrones et pilotées par les événements, l’accès aux états épinglés et interrompus, ainsi que l’accès aux propriétés des pilotes série.

**ServiceController**

Crée une instance du composant <xref:System.ServiceProcess.ServiceController> que vous pouvez utiliser pour manipuler des services existants, notamment pour démarrer et arrêter des services, ainsi que pour envoyer des commandes vers ceux-ci.

**Minuteur**

Crée une instance du composant <xref:System.Windows.Forms.Timer> que vous pouvez utiliser pour ajouter une fonctionnalité à durée définie à vos applications Windows. Pour plus d’informations, consultez [Timer Component](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Il existe également un composant <xref:System.Timers.Timer> basé sur le système que vous pouvez ajouter à la **boîte à outils**. Ce <xref:System.Timers.Timer> est optimisé pour les applications serveur. Le <xref:System.Windows.Forms.Timer> Windows Forms, quant à lui, convient mieux à une utilisation sur les Windows Forms.

## <a name="see-also"></a>Voir aussi

- [Contrôles à utiliser sur Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Choisir des éléments de boîte à outils, composants WPF](choose-toolbox-items-wpf-components.md)
- [Boîte à outils](../../ide/reference/toolbox.md)
