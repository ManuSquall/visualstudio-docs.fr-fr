---
title: "&lt;déploiement&gt; élément (déploiement ClickOnce) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
helpviewer_keywords: <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: "30"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: ddcdc96095775f5957fbc9db872b51396798ba52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;déploiement&gt; élément (déploiement ClickOnce)
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
 L’élément `deployment` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v1`. L’élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`install`|Obligatoire. Spécifie si cette application définit une présence sur les fenêtres **Démarrer** menu et dans le panneau **Ajout / Suppression de programmes** application. Les valeurs valides sont `true` et `false`. Si `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exécutera toujours la version la plus récente de cette application à partir du réseau et ne peut pas reconnaître le `subscription` élément.|  
|`minimumRequiredVersion`|Facultatif. Spécifie la version minimale de cette application peut s’exécuter sur le client. Si le numéro de version de l’application est inférieur au nombre de la version fourni dans le manifeste de déploiement, l’application ne s’exécutera pas. Numéros de version doivent être spécifiés dans le format `N.N.N.N`, où `N` est un entier non signé. Si le `install` attribut est `false`, `minimumRequiredVersion` ne doit pas être définie.|  
|`mapFileExtensions`|Facultatif. La valeur par défaut est `false`. Si `true`, tous les fichiers dans le déploiement doivent avoir une extension .deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]supprimera cette extension de ces fichiers dès qu’il les télécharge à partir du serveur Web. Si vous publiez votre application à l’aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il ajoute automatiquement cette extension à tous les fichiers. Ce paramètre permet à tous les fichiers dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement à être téléchargés à partir d’un serveur Web qui bloque la transmission des fichiers se terminant par « unsafe » extensions telles que .exe.|  
|`disallowUrlActivation`|Facultatif. La valeur par défaut est `false`. Si `true`, empêche une application installée en cours de démarrage en cliquant sur l’URL ou en entrant l’URL dans Internet Explorer. Si le `install` attribut n’est pas présent, cet attribut est ignoré.|  
|`trustURLParameters`|Facultatif. La valeur par défaut est `false`. Si `true`quantité comme arguments de ligne de commande sont passés à une application de ligne de commande, permet à l’URL de contenir des paramètres de chaîne de requête qui sont passés à l’application. Pour plus d’informations, consultez [Comment : récupérer des informations de chaîne de requête dans une Application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si le `disallowUrlActivation` attribut est `true`, `trustUrlParameters` doit être exclu du manifeste, ou explicitement la valeur `false`.|  
  
 Le `deployment` élément contient également les éléments enfants suivants.  
  
## <a name="subscription"></a>Abonnement  
 Facultatif. Contient le `update` élément. Le `subscription` élément ne possède pas d’attributs. Si le `subscription` élément n’existe pas, le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application ne vérifie jamais les mises à jour. Si le `install` attribut de la `deployment` élément est `false`, le `subscription` élément est ignoré, car un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application qui est lancée à partir du réseau toujours utilise la version la plus récente.  
  
## <a name="update"></a>update  
 Requis. Cet élément est un enfant de la `subscription` élément et contient le `beforeApplicationStartup` ou `expiration` élément. `beforeApplicationStartup`et `expiration` ne peut pas être spécifiés dans le même manifeste de déploiement.  
  
 Le `update` élément ne possède pas d’attributs.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Facultatif. Cet élément est un enfant de le `update` élément et n’a aucun attribut. Lorsque le `beforeApplicationStartup` élément existe, l’application peut être bloqué quand [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vérifie les mises à jour, si le client est en ligne. Si cet élément n’existe pas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] commence par vérifier les mises à jour selon les valeurs spécifiées pour le `expiration` élément. `beforeApplicationStartup`et `expiration` ne peut pas être spécifiés dans le même manifeste de déploiement.  
  
## <a name="expiration"></a>expiration  
 Facultatif. Cet élément est un enfant de le `update` élément, et n’a pas d’enfants. `beforeApplicationStartup`et `expiration` ne peut pas être spécifiés dans le même manifeste de déploiement. Lors de la vérification de la mise à jour se produit et une version mise à jour est détectée, la nouvelle version met en cache pendant l’exécution de la version existante. La nouvelle version, puis installe le prochain lancement de le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.  
  
 Le `expiration` élément prend en charge les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maximumAge`|Obligatoire. Identifie l’ancienneté la mise à jour en cours doit devenir avant que l’application effectue une vérification de mise à jour. L’unité de temps est déterminée par la `unit` attribut.|  
|`unit`|Obligatoire. Identifie l’unité de temps pour `maximumAge`. Les unités valides sont `hours`, `days`, et `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Pour le .NET Framework 2.0, cet élément est requis si le manifeste de déploiement contient un `subscription` section. Pour le .NET Framework 3.5 et versions ultérieures, cet élément est facultatif et par défaut pour le serveur et le chemin d’accès du fichier dans lequel le manifeste de déploiement a été détecté.  
  
 Cet élément est un enfant de l’élément `deployment` et contient l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`codebase`|Obligatoire. Identifie l’emplacement, comme une ressource identificateur URI (Uniform), du manifeste de déploiement qui est utilisé pour mettre à jour le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Cet élément permet également de transférer les emplacements de mise à jour pour les installations basées sur le CD. Doit être un URI valide.|  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez configurer votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application pour rechercher les mises à jour au démarrage, vérifier les mises à jour après le démarrage ou ne jamais rechercher les mises à jour. Pour vérifier les mises à jour au démarrage, assurez-vous que le `beforeApplicationStartup` élément existe sous le `update` élément. Pour vérifier les mises à jour après le démarrage, assurez-vous que le `expiration` élément existe sous le `update` élément, et que les intervalles de mise à jour sont fournies.  
  
 Pour désactiver la vérification des mises à jour, supprimez le `subscription` élément. Lorsque vous spécifiez dans le manifeste de déploiement pour ne jamais vérifier les mises à jour, vous pouvez vérifier manuellement les mises à jour à l’aide de la <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> (méthode).  
  
 Pour plus d’informations sur la façon dont le deploymentProvider est lié aux mises à jour, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple de code suivant illustre un `deployment` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. L’exemple utilise un `deploymentProvider` élément pour indiquer l’emplacement de mise à jour par défaut.  
  
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