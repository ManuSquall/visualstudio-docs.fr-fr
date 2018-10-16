---
title: '&lt;point d’entrée&gt; , élément (Application ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: da308de644dfc73d9364b65e21e820d6fc6c2a8a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255311"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;point d’entrée&gt; , élément (Application ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifie l’assembly qui doit être exécutée lorsque cela [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application est exécutée sur un ordinateur client.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `entryPoint` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v2` . Il peut être uniquement un `entryPoint` élément défini dans un manifeste d’application.  
  
 L’élément `entryPoint` comporte l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Facultatif. Cette valeur n’est pas utilisée par .NET Framework.|  
  
 `entryPoint` comporte les éléments suivants.  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. Le rôle de `assemblyIdentity` et ses attributs est défini dans [ \<assemblyIdentity > élément](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 Le `processorArchitecture` attribut de cet élément et le `processorArchitecture` attribut défini dans le `assemblyIdentity` ailleurs dans l’application manifeste doit correspondre.  
  
## <a name="commandline"></a>ligne de commande  
 Obligatoire. Doit être un enfant de le `entryPoint` élément. Il ne comporte aucun élément enfant et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`file`|Obligatoire. Une référence locale à l’assembly de démarrage pour le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Cette valeur ne peut pas contenir de barre oblique (/) ou barre oblique inverse (\\) les séparateurs de chemin d’accès.|  
|`parameters`|Obligatoire. Décrit l’action à entreprendre avec le point d’entrée. La seule valeur valide est `run`; si une chaîne vide est fournie, `run` est supposé.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Facultatif. Si inclus, spécifie que ce déploiement contient un composant qui sera déployé sur un hôte personnalisé et n’est pas une application autonome.  
  
 Si cet élément est présent, le `assemblyIdentity` et `commandLine` éléments ne doivent pas être présents. S’ils sont, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déclenchera une erreur de validation pendant l’installation.  
  
 Cet élément possède pas d’attributs et aucun enfant.  
  
## <a name="customux"></a>customUX  
 Facultatif. Spécifie que l’application est installée et géré par un programme d’installation personnalisé et ne pas créer une entrée de menu Démarrer, raccourci ou ajouter ou supprimer l’entrée de programmes.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Une application qui inclut l’élément de customUX doit fournir un programme d’installation personnalisé qui utilise le <xref:System.Deployment.Application.InPlaceHostingManager> classe pour effectuer des opérations d’installation. Une application avec cet élément ne peut pas être installée en double-cliquant sur son manifeste ou setup.exe prérequis du programme d’amorçage. Le programme d’installation personnalisé peut créer des entrées de menu Démarrer, les raccourcis et les entrées d’Ajout / Suppression de programmes. Si le programme d’installation personnalisé ne crée pas une entrée Ajout / Suppression de programmes, elle doit stocker l’identificateur d’abonnement fourni par le <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> propriété et activez l’utilisateur pour désinstaller l’application ultérieurement en appelant le <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> (méthode). Pour plus d’informations, consultez [procédure pas à pas : création d’un programme d’installation personnalisé pour une Application ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Notes  
 Cet élément identifie l’assembly point d’entrée pour le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
 Vous ne pouvez pas utiliser `commandLine` pour passer des paramètres à votre application au moment de l’exécution. Vous pouvez accéder à des paramètres de chaîne de requête pour un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement à partir de l’application <xref:System.AppDomain>. Pour plus d’informations, consultez [Comment : récupérer des informations de chaîne de requête dans une Application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un `entryPoint` élément dans un manifeste d’application pour un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Cet exemple de code fait partie d’un exemple plus complet fourni pour le [manifeste d’Application ClickOnce](../deployment/clickonce-application-manifest.md) rubrique.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)



