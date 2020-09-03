---
title: '&lt;Deployment &gt; , élément (déploiement ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a55b5519d5abb7b40aeca23fed1bc2f8ea2cc33d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194641"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Deployment &gt; , élément (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifie les attributs utilisés pour le déploiement de mises à jour et l'exposition au système.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `deployment` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v1` . L’élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`install`|Obligatoire. Spécifie si cette application définit une présence dans le menu **Démarrer** de Windows et dans l’application **Ajout/suppression de programmes** du panneau de configuration. Les valeurs valides sont `true` et `false`. Si `false` , [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] exécute toujours la version la plus récente de cette application à partir du réseau et ne reconnaît pas l' `subscription` élément.|  
|`minimumRequiredVersion`|facultatif. Spécifie la version minimale de cette application qui peut s’exécuter sur le client. Si le numéro de version de l’application est inférieur au numéro de version fourni dans le manifeste de déploiement, l’application ne s’exécute pas. Les numéros de version doivent être spécifiés au format `N.N.N.N` , où `N` est un entier non signé. Si l' `install` attribut a `false` la `minimumRequiredVersion` valeur, ne doit pas être défini.|  
|`mapFileExtensions`|facultatif. La valeur par défaut est `false`. Si `true` , tous les fichiers du déploiement doivent avoir une extension. deploy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] supprime cette extension de ces fichiers dès qu’elle les télécharge à partir du serveur Web. Si vous publiez votre application à l’aide de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , elle ajoute automatiquement cette extension à tous les fichiers. Ce paramètre permet à tous les fichiers d’un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement d’être téléchargés à partir d’un serveur Web qui bloque la transmission de fichiers se terminant par des extensions « non sécurisées » telles que. exe.|  
|`disallowUrlActivation`|facultatif. La valeur par défaut est `false`. Si `true` la, empêche le démarrage d’une application installée en cliquant sur l’URL ou en entrant l’URL dans Internet Explorer. Si l' `install` attribut n’est pas présent, cet attribut est ignoré.|  
|`trustURLParameters`|facultatif. La valeur par défaut est `false`. Si `true` la valeur est, autorise l’URL à contenir des paramètres de chaîne de requête qui sont passés à l’application, tout comme les arguments de ligne de commande passés à une application de ligne de commande. Pour plus d’informations, consultez [Comment : récupérer des informations de chaîne de requête dans une application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si l' `disallowUrlActivation` attribut a `true` la `trustUrlParameters` valeur, doit être exclu du manifeste ou défini explicitement sur `false` .|  
  
 L' `deployment` élément contient également les éléments enfants suivants.  
  
## <a name="subscription"></a>subscription  
 facultatif. Contient l' `update` élément. L’élément `subscription` ne comporte pas d’attributs. Si l' `subscription` élément n’existe pas, l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application ne recherchera jamais les mises à jour. Si l' `install` attribut de l' `deployment` élément est `false` , l' `subscription` élément est ignoré, car une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application lancée à partir du réseau utilise toujours la version la plus récente.  
  
## <a name="update"></a>update  
 Obligatoire. Cet élément est un enfant de l' `subscription` élément et contient l' `beforeApplicationStartup` `expiration` élément ou. `beforeApplicationStartup` et `expiration` ne peuvent pas être spécifiés dans le même manifeste de déploiement.  
  
 L’élément `update` ne comporte pas d’attributs.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 facultatif. Cet élément est un enfant de l' `update` élément et n’a pas d’attributs. Lorsque l' `beforeApplicationStartup` élément existe, l’application est bloquée lors [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] de la recherche de mises à jour, si le client est en ligne. Si cet élément n’existe pas, commence [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] par Rechercher les mises à jour en fonction des valeurs spécifiées pour l' `expiration` élément. `beforeApplicationStartup` et `expiration` ne peuvent pas être spécifiés dans le même manifeste de déploiement.  
  
## <a name="expiration"></a>expiration  
 facultatif. Cet élément est un enfant de l' `update` élément et n’a pas d’enfants. `beforeApplicationStartup` et `expiration` ne peuvent pas être spécifiés dans le même manifeste de déploiement. Lorsque la vérification de mise à jour se produit et qu’une version mise à jour est détectée, la nouvelle version met en cache pendant l’exécution de la version existante. La nouvelle version s’installe ensuite au lancement suivant de l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
 L' `expiration` élément prend en charge les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maximumAge`|Obligatoire. Identifie l’ancienneté de la mise à jour actuelle avant que l’application effectue une vérification des mises à jour. L’unité de temps est déterminée par l' `unit` attribut.|  
|`unit`|Obligatoire. Identifie l’unité de temps pour `maximumAge` . Les unités valides sont `hours` , `days` et `weeks` .|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Pour la .NET Framework 2,0, cet élément est requis si le manifeste de déploiement contient une `subscription` section. Pour le .NET Framework 3,5 et versions ultérieures, cet élément est facultatif, et est par défaut le chemin d’accès au serveur et au fichier dans lequel le manifeste de déploiement a été découvert.  
  
 Cet élément est un enfant de l’élément `deployment` et contient l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`codebase`|Obligatoire. Identifie l’emplacement, sous la forme d’un Uniform Resource Identifier (URI), du manifeste de déploiement utilisé pour mettre à jour l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Cet élément permet également de transférer des emplacements de mise à jour pour les installations sur CD. Doit être un URI valide.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez configurer votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application pour rechercher les mises à jour au démarrage, rechercher les mises à jour après le démarrage ou ne jamais Rechercher les mises à jour. Pour rechercher les mises à jour au démarrage, assurez-vous que l' `beforeApplicationStartup` élément existe sous l' `update` élément. Pour rechercher les mises à jour après le démarrage, assurez-vous que l' `expiration` élément existe sous l' `update` élément et que des intervalles de mise à jour sont fournis.  
  
 Pour désactiver la vérification des mises à jour, supprimez l' `subscription` élément. Lorsque vous spécifiez dans le manifeste de déploiement de ne jamais Rechercher les mises à jour, vous pouvez toujours rechercher manuellement les mises à jour à l’aide de la <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> méthode.  
  
 Pour plus d’informations sur le lien entre le deploymentProvider et les mises à jour, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple de code suivant illustre un `deployment` élément dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste de déploiement. L’exemple utilise un `deploymentProvider` élément pour indiquer l’emplacement de mise à jour par défaut.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
