---
title: Journalisation dans un environnement multiprocesseur | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
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
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e78d6c35fa294d2f1a39c91af5e278e9e4519d2d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="logging-in-a-multi-processor-environment"></a>Journalisation dans un environnement multiprocesseur
La capacité de MSBuild à utiliser plusieurs processeurs peut réduire considérablement la durée de génération de projet, mais il ajoute également la complexité à la journalisation. Dans un environnement à un seul processeur, l’enregistreur d’événements peut gérer entrant des événements, messages, avertissements et erreurs de façon prévisible et séquentielle. Toutefois, dans un environnement multiprocesseur, les événements provenant de plusieurs sources peuvent arriver simultanément ou hors séquence. MSBuild fournit un nouvel enregistreur d’événements prenant en charge plusieurs processeurs et permet la création de personnalisé « journaux de transfert. »  
  
## <a name="logging-multiple-processor-builds"></a>Journalisation multiprocesseur de Builds  
 Lorsque vous créez un ou plusieurs projets dans un système multiprocesseur ou multicœur, MSBuild événements de build pour tous les projets sont générés simultanément. Une montagne de données d’événement peut arriver à l’enregistreur d’événements en même temps ou hors séquence. Cela peut saturer et entraîner des durées de génération accrue, la sortie de journal incorrect ou même une version. Pour résoudre ces problèmes, l’enregistreur d’événements de MSBuild peut traiter les événements de sortie de la séquence et mettre en corrélation les événements et leurs sources.  
  
 Vous pouvez améliorer l’efficacité de journalisation en créant un journal de transfert personnalisé. Un journal de transfert personnalisé agit comme un filtre en vous permettant de choisir, avant de générer, les événements que vous souhaitez analyser. Lorsque vous utilisez un journal de transfert personnalisé, les événements indésirables ne pas saturer, vos journaux ou ralentir la génération.  
  
### <a name="central-logging-model"></a>Modèle de journalisation central  
 Pour les builds multiprocesseurs, MSBuild utilise un « modèle de journalisation central ». Dans le modèle de journalisation central, une instance de MSBuild.exe agit comme le processus de génération principal, ou « nœud central ». Les instances secondaires de MSBuild.exe, ou « nœuds secondaires », sont attachés au nœud central. Tous les journaux en fonction de ILogger attachés au nœud central sont appelés « journaux centraux » et les enregistreurs d’événements liés à des nœuds secondaires sont appelés « journaux secondaires ».  
  
 En cas d’une build, les journaux secondaires dirigent leur trafic d’événement vers les journaux centraux. Étant donné que les événements proviennent de plusieurs nœuds secondaires, les données arrivent simultanément au niveau du nœud central mais entrelacement. Pour résoudre les références de projet de l’événement et les événements à la cible, les arguments d’événement incluent des informations de contexte d’événement génération supplémentaires.  
  
 Même si seules <xref:Microsoft.Build.Framework.ILogger> est requis pour être implémenté par le journal central, nous vous recommandons d’implémenter également <xref:Microsoft.Build.Framework.INodeLogger> si vous souhaitez que l’enregistreur d’événements central pour initialiser le nombre de nœuds qui participent à la build. La surcharge suivante de la <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> méthode est appelée lorsque le moteur initialise le journal :  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Modèle d'enregistrement distribué  
 Dans le modèle de journalisation central, trop de trafic entrant de message, par exemple lorsque de nombreux projets génèrent à la fois, permettre surcharger le nœud central, ce qui affecte le système et réduit les performances de génération.  
  
 Pour réduire ce problème, MSBuild active également un « modèle de journalisation distribué » qui étend le modèle de journalisation central en vous permettant de créer des journaux de transfert. Un journal de transfert est attaché à un nœud secondaire et reçoit des événements de build entrants de ce nœud. Le journal de transfert est comme un journal normal mais peut filtrer les événements et puis transférer uniquement ceux souhaité au nœud central. Cela réduit le trafic des messages au niveau du nœud central et permet ainsi de meilleures performances.  
  
 Vous pouvez créer un journal de transfert en implémentant la <xref:Microsoft.Build.Framework.IForwardingLogger> interface, qui dérive de <xref:Microsoft.Build.Framework.ILogger>. L’interface est définie en tant que :  
  
```csharp
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Pour transférer des événements dans un journal de transfert, appelez le <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> méthode de la <xref:Microsoft.Build.Framework.IEventRedirector> interface. Passez les <xref:Microsoft.Build.Framework.BuildEventArgs>, ou un dérivatif, comme paramètre.  
  
 Pour plus d’informations, consultez [création enregistreurs d’événements de transfert](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Joindre un journal distribué  
 Pour joindre un journal distribué sur une version de ligne de commande, utilisez le `/distributedlogger` (ou, `/dl` en abrégé) basculer. Le format pour spécifier les noms de types de l’enregistreur d’événements et des classes sont les mêmes que celles pour la `/logger` basculer, à ceci près qu’un journal distribué se compose de deux classes d’enregistrement : un journal de transfert et le journal central. Voici un exemple de joindre un journal distribué :  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Un astérisque (*) sépare les deux noms de journal dans le `/dl` basculer.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistreurs d’événements de génération](../msbuild/build-loggers.md)   
 [Création d’enregistreurs d’événements de transfert](../msbuild/creating-forwarding-loggers.md)
