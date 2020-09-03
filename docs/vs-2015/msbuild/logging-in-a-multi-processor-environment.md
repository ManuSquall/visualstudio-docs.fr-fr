---
title: Journalisation dans un environnement multiprocesseur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35184f6ef724a9f0e803a10c9bda2c6981313ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205979"
---
# <a name="logging-in-a-multi-processor-environment"></a>Journalisation dans un environnement multiprocesseur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La capacité de MSBuild à utiliser plusieurs processeurs peut fortement diminuer le temps de génération d’un projet. Elle rend cependant plus complexe la journalisation. Dans un environnement à un seul processeur, le journal (logger) peut gérer les événements entrants, les messages, les avertissements et les erreurs de façon prévisible et séquentielle. Cependant, dans un environnement multiprocesseur, des événements provenant de différentes sources peuvent arriver simultanément ou dans le désordre. MSBuild fournit un nouveau journal prenant en charge plusieurs processeurs et permet la création « de journaux de transfert » personnalisés.  
  
## <a name="logging-multiple-processor-builds"></a>Journalisation de builds multiprocesseurs  
 Quand vous générez un ou plusieurs projets sur un système multiprocesseur ou multicœur, des événements de génération de MSBuild de tous les projets sont générés simultanément. De très nombreuses données d’événements peuvent arriver au journal en même temps ou dans le désordre. Ceci peut le submerger et aboutir à des temps de génération plus longs, à une sortie incorrecte du journal ou même à une génération incorrecte. Pour résoudre ces problèmes, le journal MSBuild peut traiter les événements qui arrivent dans le désordre et associer les événements à leur source.  
  
 Vous pouvez améliorer l’efficacité de la journalisation en créant un journal de transfert personnalisé. Un journal de transfert personnalisé agit comme un filtre en vous permettant de sélectionner, avant la génération, les événements que vous voulez suivre. Quand vous utilisez un journal de transfert personnalisé, les événements non souhaités ne le saturent pas, ne polluent pas vos journaux et ne ralentissent pas la génération.  
  
### <a name="central-logging-model"></a>Modèle de journalisation centralisé  
 Pour les générations multiprocesseurs, MSBuild utilise un « modèle de journalisation centralisé ». Dans le modèle de journalisation centralisé, une instance de MSBuild.exe agit comme processus de génération principal, ou « nœud central ». Les instances secondaires de MSBuild.exe, ou « nœuds secondaires », sont attachées au nœud central. Tous les journaux ILogger attachés au nœud central sont appelés « journaux centraux » et les journaux attachés à des nœuds secondaires sont appelés « journaux secondaires ».  
  
 Quand une génération se produit, les journaux secondaires routent leur trafic vers les journaux centraux. Comme les événements proviennent de plusieurs nœuds secondaires, les données arrivent au nœud central simultanément mais entrelacés. Pour résoudre les références d’événement à projet et d’événement à cible, les arguments des événements incluent des informations de contexte d’événement de génération supplémentaires.  
  
 Même si seul <xref:Microsoft.Build.Framework.ILogger> doit être implémenté par le journal central, nous vous recommandons d’implémenter également <xref:Microsoft.Build.Framework.INodeLogger> si vous voulez que le journal central soit initialisé avec le nombre de nœuds qui participent à la génération. La surcharge suivante de la méthode <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> est appelée quand le moteur initialise le journal :  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Modèle d'enregistrement distribué  
 Dans le modèle de journalisation centralisé, un trafic de messages entrants trop important, par exemple quand de nombreux projets sont générés à la fois, peut submerger le nœud central, ce qui affecte défavorablement le système et réduit les performances de la génération.  
  
 Pour limiter ce problème, MSBuild active également un « modèle de journalisation distribué », qui étend le modèle de journalisation centralisé en vous permettant de créer des journaux de transfert. Un journal de transfert est attaché à un nœud secondaire et reçoit les événements de génération entrants de ce nœud. Le journal de transfert est comme un journal normal, sauf qu’il peut filtrer les événements et transférer seulement les événements souhaités au nœud central. Ceci réduit le trafic de messages au niveau du nœud central et permet ainsi de meilleures performances.  
  
 Vous pouvez créer un journal de transfert en implémentant l’interface <xref:Microsoft.Build.Framework.IForwardingLogger>, qui dérive de <xref:Microsoft.Build.Framework.ILogger>. L’interface est définie comme suit :  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Pour transférer des événements dans un journal de transfert, appelez la méthode <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> de l’interface <xref:Microsoft.Build.Framework.IEventRedirector>. Passez les <xref:Microsoft.Build.Framework.BuildEventArgs> appropriés, ou un dérivé, comme paramètre.  
  
 Pour plus d’informations, consultez [création de journaux de transfert](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Attacher un journal distribué  
 Pour attacher un journal distribué sur une génération en ligne de commande, utilisez le commutateur `/distributedlogger` (ou sa version abrégée `/dl`). Le format de nom des types et des classes de journal est le même que celui du commutateur `/logger`, sauf qu’un journal distribué a toujours deux classes de journalisation au lieu d’une : un journal de transfert et un journal central. Voici un exemple d’attachement d’un journal distribué :  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Un astérisque (*) sépare les deux noms de journaux dans le commutateur `/dl`.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistreurs de build](../msbuild/build-loggers.md)   
 [Création de journaux de transfert](../msbuild/creating-forwarding-loggers.md)
