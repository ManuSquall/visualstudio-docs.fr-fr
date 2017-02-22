---
title: "Logging in a Multi-Processor Environment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, multi-processor logging"
  - "MSBuild, logging"
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Logging in a Multi-Processor Environment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La capacité multi\-processeur de MSBuild peut réduire considérablement la durée de génération d'un projet, mais accentue aussi la complexité de journalisation.  Dans un environnement à processeur unique, les événements, messages, avertissements et erreurs arrivent aux journaux de façon prévisible et séquentielle.  Toutefois, dans un environnement multi\-processeur, les événements de plusieurs sources peuvent arriver simultanément ou en désordre.  MSBuild fournit un nouvel enregistreur d'événements multiprocesseur et permet la création de « journaux de transfert » personnalisés.  
  
## Enregistrement de générations avec plusieurs processeurs  
 Lors de la génération d'un ou de plusieurs projets sur un système multiprocesseur ou multicœur, les événements MSBuild de tous les projets sont générés simultanément.  Une avalanche de données d'événement peut arriver au journal en même temps ou hors séquence.  Cela peut encombrer le journal et provoquer l'augmentation du temps de génération, une sortie de journal incorrecte, ou même une génération corrompue.  Pour résoudre ces problèmes, le journal d'événement MSBuild peut traiter des événements hors séquence ou les mettre en corrélation avec leurs sources.  
  
 Vous pouvez améliorer l'efficacité de journalisation en créant un journal de transfert personnalisé.  Un journal de transfert personnalisé agit comme un filtre vous permettant de choisir, avant la génération, les événements à contrôler.  Avec un journal de transfert personnalisé, les événements inutiles ne viennent pas saturer vos journaux ni ralentir la génération.  
  
### Modèle de journalisation central  
 Pour la génération multi\-processeur, MSBuild utilise un « modèle de journalisation central ». Dans ce modèle, une instance de MSBuild.exe sert de processus de génération principal, ou « nœud central ». Les instances secondaires de MSBuild.exe, ou « nœuds secondaires », sont jointes au nœud central.  Tous les journaux au nœud central sont appelés comme « journaux centraux » et les journaux joints aux nœuds secondaires sont nommés « journaux secondaires ».  
  
 Lorsqu'une génération se produit, les journaux secondaires dirigent leur trafic d'événement vers les journaux centraux.  Comme les événements proviennent de plusieurs nœuds secondaires, les données arrivent simultanément au nœud central mais sont entrelacés.  Pour résoudre les références événement\-à\-projet et événement\-à\-cible, les arguments d'événement incluent des informations de contexte d'événement de build supplémentaires.  
  
 Si le journal central ne soit d'implémenter que <xref:Microsoft.Build.Framework.ILogger>, il est toutefois recommandé d'implémenter également <xref:Microsoft.Build.Framework.INodeLogger> pour initialiser le journal central avec le nombre des nœuds qui participent à la génération.  La surcharge suivante de la méthode <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> est appelée lorsque le moteur initialise le journal :  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### Modèle de journalisation distribué  
 Avec le modèle de journalisation central, un trafic entrant trop volumineux comme c'est le cas lors de la génération simultanée de plusieurs projets, peut encombrer le nœud central et saturer le système en réduisant les performances de génération.  
  
 Pour réduire ce problème, MSBuild active également un « modèle de journalisation distribué » qui étend le modèle de journalisation central en vous laissant créer des journaux de transfert.  Un journal de transfert est joint à un nœud secondaire et reçoit des événements de build entrants de ce nœud.  Le journal de transfert est comparable à un journal normal mais peut filtrer les événements et envoyer les événements appropriés au nœud central.  Il réduit ainsi le trafic de messages destiné au nœud central et par conséquent accélère les performances.  
  
 Vous pouvez créer un journal de transfert en implémentant l'interface <xref:Microsoft.Build.Framework.IForwardingLogger>, qui dérive de <xref:Microsoft.Build.Framework.ILogger>.  L'interface se définit de la manière suivante :  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Pour transférer les événements vers un journal de transfert, appelez la méthode <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> de l'interface <xref:Microsoft.Build.Framework.IEventRedirector>.  Passez le <xref:Microsoft.Build.Framework.BuildEventArgs>approprié, ou un dérivatif, comme paramètre.  
  
 Pour plus d'informations, consultez [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md).  
  
### Journal distribué joint  
 Pour joindre un journal distribué sur une génération de ligne de commande, utilisez le commutateur `/distributedlogger` \(ou, `/dl` en abrégé\).  Le format à utiliser pour spécifier les noms des types de journaux et les classes est le même que celui du commutateur `/logger`, mais un journal distribué se compose de deux classes de journalisation, le journal de transfert et le journal central.  L'exemple suivant illustre comment joindre un journal distribué :  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Un astérisque \(\*\) sépare les deux noms de journal dans le commutateur `/dl`.  
  
## Voir aussi  
 [Build Loggers](../msbuild/build-loggers.md)   
 [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md)