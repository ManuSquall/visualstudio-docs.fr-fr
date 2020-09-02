---
title: '&lt;entryPoint &gt; , élément (application ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 615a606dc4d04682a9d5a1a69c91b4d2cd67de15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928609"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint &gt; , élément (application ClickOnce)
Identifie l’assembly qui doit être exécuté lorsque cette [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est exécutée sur un ordinateur client.

## <a name="syntax"></a>Syntaxe

```xml
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
 L’élément `entryPoint` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v2` . Il ne peut y avoir qu’un seul `entryPoint` élément défini dans un manifeste d’application.

 L’élément `entryPoint` comporte l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`name`|facultatif. Cette valeur n’est pas utilisée par .NET Framework.|

 `entryPoint` comporte les éléments suivants.

## <a name="assemblyidentity"></a>assemblyIdentity
 Obligatoire. Le rôle de `assemblyIdentity` et de ses attributs est défini dans l' [ \<assemblyIdentity> élément](../deployment/assemblyidentity-element-clickonce-application.md).

 L' `processorArchitecture` attribut de cet élément et l' `processorArchitecture` attribut défini dans un `assemblyIdentity` autre emplacement du manifeste de l’application doivent correspondre.

## <a name="commandline"></a>commandLine
 Obligatoire. Doit être un enfant de l' `entryPoint` élément. Il n’a pas d’éléments enfants et a les attributs suivants.

| Attribut | Description |
|--------------| - |
| `file` | Obligatoire. Référence locale à l’assembly de démarrage pour l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Cette valeur ne peut pas contenir de séparateurs de chemin d’accès (/) ou de barre oblique inverse ( \\ ). |
| `parameters` | Obligatoire. Décrit l’action à effectuer avec le point d’entrée. La seule valeur valide est `run` ; si une chaîne vide est fournie, `run` est utilisé par défaut. |

## <a name="customhostrequired"></a>customHostRequired
 facultatif. Si inclus, spécifie que ce déploiement contient un composant qui sera déployé au sein d’un hôte personnalisé et qui n’est pas une application autonome.

 Si cet élément est présent, les `assemblyIdentity` éléments et ne `commandLine` doivent pas être présents. Si c’est le cas, génère [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] une erreur de validation lors de l’installation.

 Cet élément n’a pas d’attributs ni d’enfants.

## <a name="customux"></a>customUX
 facultatif. Spécifie que l’application est installée et gérée par un programme d’installation personnalisé et ne crée pas d’entrée de menu Démarrer, de raccourci ou d’ajout/suppression de programmes.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Une application qui comprend l’élément customUX doit fournir un programme d’installation personnalisé qui utilise la <xref:System.Deployment.Application.InPlaceHostingManager> classe pour effectuer des opérations d’installation. Une application avec cet élément ne peut pas être installée en double-cliquant sur son manifeste ou setup.exe programme d’amorçage de la configuration requise. Le programme d’installation personnalisé peut créer des entrées de menu Démarrer, des raccourcis et des entrées ajout/suppression de programmes. Si le programme d’installation personnalisé ne crée pas d’entrée ajout/suppression de programmes, il doit stocker l’identificateur d’abonnement fourni par la <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> propriété et permettre à l’utilisateur de désinstaller l’application ultérieurement en appelant la <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> méthode. Pour plus d’informations, consultez [procédure pas à pas : création d’un programme d’installation personnalisé pour une application ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Notes
 Cet élément identifie l’assembly et le point d’entrée de l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

 Vous ne pouvez pas utiliser `commandLine` pour passer des paramètres dans votre application au moment de l’exécution. Vous pouvez accéder aux paramètres de chaîne de requête pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement à partir de l’application <xref:System.AppDomain> . Pour plus d’informations, consultez [Comment : récupérer des informations de chaîne de requête dans une application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre un `entryPoint` élément dans un manifeste d’application pour une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Cet exemple de code fait partie d’un exemple plus complet fourni pour la rubrique du [manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
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
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
