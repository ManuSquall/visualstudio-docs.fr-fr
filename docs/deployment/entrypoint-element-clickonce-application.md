---
title: '&lt;point d’entrée&gt; élément (déploiement ClickOnce) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: cd263d8137b380519477d16079e8ed8b1547fbbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;point d’entrée&gt; élément (déploiement ClickOnce)
Identifie l’assembly qui doit être exécutée lorsque cela [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est exécutée sur un ordinateur client.  
  
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
 L’élément `entryPoint` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v2`. Il peut être uniquement un `entryPoint` élément défini dans un manifeste d’application.  
  
 Le `entryPoint` élément a l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Facultatif. Cette valeur n’est pas utilisée par le .NET Framework.|  
  
 `entryPoint` contient les éléments suivants.  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. Le rôle de `assemblyIdentity` et ses attributs est défini dans [ \<assemblyIdentity > élément](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 Le `processorArchitecture` attribut de cet élément et la `processorArchitecture` attribut défini dans le `assemblyIdentity` ailleurs dans l’application manifeste doit correspondre.  
  
## <a name="commandline"></a>Ligne de commande  
 Obligatoire. Doit être un enfant de le `entryPoint` élément. Il ne comporte aucun élément enfant et possède les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`file`|Obligatoire. Une référence locale à l’assembly de démarrage pour le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Cette valeur ne peut pas contenir de barre oblique (/) ou barre oblique inverse (\\) comme séparateur de chemin d’accès.|  
|`parameters`|Obligatoire. Décrit l’action à effectuer avec le point d’entrée. La seule valeur valide est `run`; si une chaîne vide est fournie, `run` est supposé.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Facultatif. Si inclus, spécifie que ce déploiement contient un composant qui sera déployé sur un hôte personnalisé et n’est pas une application autonome.  
  
 Si cet élément est présent, le `assemblyIdentity` et `commandLine` éléments ne doivent pas être présents. S’ils sont, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] génère une erreur de validation lors de l’installation.  
  
 Cet élément a pas d’attributs et aucun enfant.  
  
## <a name="customux"></a>customUX  
 Facultatif. Spécifie que l’application est installée et maintenu par un programme d’installation personnalisé et ne pas créer une entrée dans le menu Démarrer, raccourci ou ajouter ou supprimer l’entrée de programmes.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Une application qui comprend l’élément customUX doit fournir un programme d’installation personnalisé qui utilise le <xref:System.Deployment.Application.InPlaceHostingManager> classe pour effectuer des opérations d’installation. Une application avec cet élément ne peut pas être installée en double-cliquant sur son manifeste ou setup.exe requis du programme d’amorçage. Le programme d’installation personnalisé peut créer des entrées du menu Démarrer, les raccourcis et entrées Ajout / Suppression de programmes. Si le programme d’installation personnalisé ne crée pas une entrée Ajout / Suppression de programmes, elle doit stocker l’identificateur d’abonnement fourni par le <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> propriété et activer l’utilisateur de désinstaller l’application plus tard en appelant le <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> (méthode). Pour plus d’informations, consultez [procédure pas à pas : création d’un programme d’installation personnalisé pour une Application ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Notes  
 Cet élément identifie l’assembly point d’entrée pour le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.  
  
 Vous ne pouvez pas utiliser `commandLine` pour passer des paramètres à votre application au moment de l’exécution. Vous pouvez accéder à des paramètres de chaîne de requête pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement à partir de l’application <xref:System.AppDomain>. Pour plus d’informations, consultez [Comment : récupérer des informations de chaîne de requête dans une Application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un `entryPoint` élément dans un manifeste d’application pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Cet exemple de code fait partie d’un exemple plus complet fourni pour le [manifeste d’Application ClickOnce](../deployment/clickonce-application-manifest.md) rubrique.  
  
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
 [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)