---
title: Écriture de journaux multiprocesseurs | Microsoft Docs
description: Découvrez comment MSBuild fournit un journal et un modèle de journalisation multiprocesseurs, et vous permet de créer des « journaux de transfert » personnalisés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd90cb92dd56d3e7ff9eb43bad1086e8a8fb548f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047303"
---
# <a name="write-multi-processor-aware-loggers"></a>Écrire des journaux multiprocesseurs

La capacité de MSBuild à tirer parti de plusieurs processeurs peut réduire le temps de génération du projet, mais il complique également la génération de la journalisation des événements. Dans un environnement à un seul processeur, les événements, messages, avertissements et erreurs arrivent au journal (logger) de manière prévisible et séquentielle. Toutefois, dans un environnement multiprocesseur, les événements provenant de différentes sources peuvent arriver en même temps ou dans le désordre. Pour ce faire, MSBuild fournit un enregistreur d’événements prenant en charge plusieurs processeurs et un nouveau modèle de journalisation, et vous permet de créer des « journaux de transfert » personnalisés.

## <a name="multi-processor-logging-challenges"></a>Difficultés liées à la journalisation multiprocesseur

 Quand vous générez un ou plusieurs projets sur un système multiprocesseur ou multicœur, les événements de build MSBuild pour tous les projets sont générés en même temps. De très nombreux messages d’événements peuvent arriver au journal d’événements en même temps ou dans le désordre. Étant donné qu’un enregistreur d’événements MSBuild 2,0 n’est pas conçu pour gérer cette situation, il peut saturer le journal et provoquer des temps de génération accrus, une sortie de journal incorrecte ou même une build endommagée. Pour résoudre ces problèmes, le journal (à partir de MSBuild 3,5) peut traiter les événements hors séquence et corréler les événements et leurs sources.

 Vous pouvez améliorer l’efficacité de la journalisation en créant un journal de transfert personnalisé. Un journal de transfert personnalisé agit comme un filtre en vous permettant de sélectionner, avant la génération, les événements que vous souhaitez suivre. Lorsque vous utilisez un journal de transfert personnalisé, vous n’avez pas d’événements inutiles qui saturent le journal, polluent vos journaux ou ralentissent la génération.

## <a name="multi-processor-logging-models"></a>Modèles de journalisation multiprocesseur

 Pour fournir des problèmes de génération liés à plusieurs processeurs, MSBuild prend en charge deux modèles de journalisation, centrale et distribuée.

### <a name="central-logging-model"></a>Modèle de journalisation centralisé

 Dans le modèle de journalisation centralisé, une seule instance de *MSBuild.exe* agit comme « nœud central », et les instances enfants du nœud central (les « nœuds secondaires ») sont jointes au nœud central pour l’aider à effectuer les tâches de génération.

 ![Modèle d'enregistreur d'événements central](../msbuild/media/centralnode.png "CentralNode")

 Les journaux de différents types qui sont joints au nœud central sont appelés « journaux centraux ». Une seule instance de chaque type de journal peut être jointe au nœud central.

 Lors d’une génération, les nœuds secondaires routent leurs événements de build vers le nœud central. Le nœud central route tous ses événements, ainsi que ceux des nœuds secondaires, vers un ou plusieurs des journaux centraux joints. Les journaux créent ensuite les fichiers journaux qui sont basés sur les données entrantes.

 Même si seul <xref:Microsoft.Build.Framework.ILogger> doit être implémenté par le journal central, nous vous recommandons d’implémenter également <xref:Microsoft.Build.Framework.INodeLogger> afin que le journal central soit initialisé avec le nombre de nœuds qui participent à la génération. La surcharge suivante de la méthode <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> émet un appel lorsque le moteur initialise le journal.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Tous les journaux <xref:Microsoft.Build.Framework.ILogger> existants peuvent agir comme des journaux centraux et peuvent être joints à la génération. Toutefois, les journaux centraux qui sont écrits sans prise en charge explicite des scénarios de journalisation multiprocesseur et des événements non ordonnés peuvent causer l’arrêt de la génération ou produire une sortie incorrecte.

### <a name="distributed-logging-model"></a>Modèle de journalisation distribué

 Dans le modèle de journalisation centralisé, un trop grand nombre de messages entrants peut saturer le nœud central, comme lorsque de nombreux projets sont générés en même temps. Cela peut provoquer une contrainte sur les ressources système et affecter les performances de génération. Pour faciliter ce problème, MSBuild prend en charge un modèle de journalisation distribué.

 ![Modèle d'enregistrement distribué](../msbuild/media/distnode.png "DistNode")

 Le modèle de journalisation distribué étend le modèle de journalisation centralisé en vous permettant de créer un journal de transfert.

#### <a name="forwarding-loggers"></a>Journaux de transfert

 Un journal de transfert est un journal léger et secondaire. Il comprend un filtre d’événement qui est joint à un nœud secondaire et qui reçoit de ce nœud des événements de build entrants. Il filtre les événements entrants et transfère uniquement ceux que vous spécifiez au nœud central. Cela réduit le trafic des messages qui sont envoyés au nœud central et améliore les performances globales de génération.

 Il existe deux façons d’utiliser la journalisation distribuée :

- Personnalisez le journal de transfert prédéfini nommé <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.

- Écrivez votre propre journal de transfert personnalisé.

Vous pouvez modifier ConfigurableForwardingLogger pour l’adapter à vos besoins. Pour ce faire, appelez le journal sur la ligne de commande à l’aide de *MSBuild.exe* et créez une liste des événements de build que le journal doit transférer au nœud central.

En guise d’alternative, vous pouvez créer un journal de transfert personnalisé. La création d’un journal de transfert personnalisé vous permet d’ajuster le comportement du journal. Toutefois, la création d’un journal de transfert personnalisé est plus complexe que la simple personnalisation de ConfigurableForwardingLogger. Pour plus d’informations, consultez [Création de journaux de transfert](../msbuild/creating-forwarding-loggers.md).

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Utilisation de ConfigurableForwardingLogger pour une journalisation distribuée simple

 Pour joindre ConfigurableForwardingLogger ou un journal de transfert personnalisé, utilisez le commutateur `-distributedlogger` (`-dl`, en abrégé) dans une build de ligne de commande *MSBuild.exe* . Le format de nom des types et des classes du journal est le même que celui du commutateur `-logger`, sauf qu’un journal distribué a toujours deux classes de journalisation au lieu d’une : le journal de transfert et le journal central. Voici un exemple dans lequel est joint un journal de transfert personnalisé nommé XMLForwardingLogger.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Un astérisque (*) doit séparer les deux noms de journaux dans le commutateur `-dl`.

 L’utilisation de ConfigurableForwardingLogger est semblable à l’utilisation d’un autre journal (comme indiqué dans [obtention des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)), à ceci près que vous attachez le journal ConfigurableForwardingLogger au lieu du journal MSBuild classique et que vous spécifiez comme paramètres les événements que vous souhaitez que le ConfigurableForwardingLogger passe au nœud central.

 Par exemple, si vous souhaitez être averti uniquement au début et à la fin d’une génération, et lorsqu’une erreur se produit, vous pouvez passer `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` et `ERROREVENT` comme paramètres. Pour passer plusieurs paramètres, séparez-les par des points-virgules. Voici un exemple d’utilisation de ConfigurableForwardingLogger pour transférer uniquement les événements `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` et `ERROREVENT`.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 Voici la liste des paramètres disponibles pour ConfigurableForwardingLogger.

|Paramètres de ConfigurableForwardingLogger|
| - |
|BUILDSTARTEDEVENT|
|BUILDFINISHEDEVENT|
|PROJECTSTARTEDEVENT|
|PROJECTFINISHEDEVENT|
|TARGETSTARTEDEVENT|
|TARGETFINISHEDEVENT|
|TASKSTARTEDEVENT|
|TASKFINISHEDEVENT|
|ERROREVENT|
|WARNINGEVENT|
|HIGHMESSAGEEVENT|
|NORMALMESSAGEEVENT|
|LOWMESSAGEEVENT|
|CUSTOMEVENT|
|COMMANDLINE|
|PERFORMANCESUMMARY|
|NOSUMMARY|
|SHOWCOMMANDLINE|

## <a name="see-also"></a>Voir aussi

- [Créer des enregistreurs d’événements de transfert](../msbuild/creating-forwarding-loggers.md)