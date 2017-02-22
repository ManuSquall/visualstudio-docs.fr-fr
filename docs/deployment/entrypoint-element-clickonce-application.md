---
title: "&lt;entryPoint&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], entryPoint element"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# &lt;entryPoint&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie l'assembly à exécuter lorsque cette application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est exécutée sur un ordinateur client.  
  
## Syntaxe  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## Éléments et attributs  
 L'élément `entryPoint` est obligatoire et se trouve dans l'espace de noms `urn:schemas-microsoft-com:asm.v2`.  Il ne peut y avoir qu'un élément `entryPoint` défini dans un manifeste d'application.  
  
 L'élément `entryPoint` a l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Facultatif.  Cette valeur n'est pas utilisée par .NET Framework.|  
  
 `entryPoint` possède les éléments suivants.  
  
## assemblyIdentity  
 Obligatoire.  Le rôle de l'élément `assemblyIdentity` et de ses attributs est défini dans [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 L'attribut `processorArchitecture` de cet élément et l'attribut `processorArchitecture` défini dans l'`assemblyIdentity`, ailleurs dans le manifeste d'application, doivent correspondre.  
  
## commandLine  
 Obligatoire.  Doit être un enfant de l'élément `entryPoint`.  Il ne contient pas d'élément enfant et possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`file`|Obligatoire.  Une référence locale à l'assembly de démarrage pour l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cette valeur ne peut pas contenir de séparateurs de chemins barre oblique \(\/\) ou barre oblique inverse \(\\\).|  
|`parameters`|Obligatoire.  Décrit l'action à effectuer avec le point d'entrée.  La seule valeur valide est `run` ; si une chaîne vide est fournie, la valeur `run` est supposée.|  
  
## customHostRequired  
 Facultatif.  Si cet attribut est utilisé, il indique que ce déploiement contient un composant qui sera déployé sur un hôte personnalisé et n'est pas une application autonome.  
  
 Si cet élément est présent, les éléments `assemblyIdentity` et `commandLine` ne doivent pas être présents.  S'ils le sont, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] génèrera une erreur de validation lors de l'installation.  
  
 Cet élément n'a pas d'attributs et aucun enfant.  
  
## customUX  
 Facultatif.  Spécifie que l'application est installée et maintenue par un programme d'installation personnalisé, et ne crée pas une entrée de menu Démarrer, un raccourci, ou une entrée Ajouter ou supprimer des programmes.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Une application qui inclut l'élément de customUX doit fournir un programme d'installation personnalisé qui utilise la classe <xref:System.Deployment.Application.InPlaceHostingManager> pour exécuter des opérations d'installation.  Une application avec cet élément ne peut pas être installée en double\-cliquant sur son manifeste ou sur setup.exe programme d'amorçage préalable.  Le programme d'installation personnalisé peut créer des entrées dans le menu Démarrer, des raccourcis et des entrées dans Ajout\/Suppression de programmes.  Si le programme d'installation personnalisé ne crée pas une entrée Ajoutez ou Supprimez les Programmes, il doit stocker l'identificateur d'abonnement fourni par la propriété <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> et activer l'utilisateur pour désinstaller ultérieurement l'application en appelant la méthode <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>.  Pour plus d'informations, consultez [Walkthrough: Creating a Custom Installer for a ClickOnce Application](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## Notes  
 Cet élément identifie l'assembly et le point d'entrée de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Vous ne pouvez pas utiliser `commandLine` pour passer des paramètres dans votre application au moment de l'exécution.  Vous pouvez accéder aux paramètres de la chaîne de requête d'un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir du <xref:System.AppDomain> de l'application.  Pour plus d'informations, consultez [Comment : récupérer les informations de chaîne de requête dans une application ClickOnce en ligne](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).  
  
## Exemple  
 L'exemple de code suivant illustre un élément `entryPoint` dans un manifeste d'application d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code fait partie d'un exemple plus développé fourni dans la rubrique [Manifeste d'application ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## Voir aussi  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)