---
title: '&lt;déploiement&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194641"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;déploiement&gt; , élément (déploiement ClickOnce)
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
|`install`|Requis. Spécifie si cette application définit une présence sur le Windows **Démarrer** menu et dans le panneau de configuration **Ajout / Suppression de programmes** application. Les valeurs valides sont `true` et `false`. Si `false`, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] exécutera toujours la dernière version de cette application à partir du réseau et ne peut pas reconnaître le `subscription` élément.|  
|`minimumRequiredVersion`|facultatif. Spécifie la version minimale de cette application peut s’exécuter sur le client. Si le numéro de version de l’application est inférieur au nombre de version fourni dans le manifeste de déploiement, l’application ne s’exécutera pas. Numéros de version doivent être spécifiés dans le format `N.N.N.N`, où `N` est un entier non signé. Si le `install` attribut est `false`, `minimumRequiredVersion` ne doit pas être définie.|  
|`mapFileExtensions`|facultatif. La valeur par défaut est `false`. Si `true`, tous les fichiers dans le déploiement doivent avoir une extension .deploy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] supprimera cette extension de ces fichiers dès qu’il les télécharge à partir du serveur Web. Si vous publiez votre application à l’aide de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], il ajoute automatiquement cette extension à tous les fichiers. Ce paramètre autorise tous les fichiers dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement être téléchargé à partir d’un serveur Web qui bloque la transmission des fichiers se terminant par « unsafe » extensions telles que .exe.|  
|`disallowUrlActivation`|facultatif. La valeur par défaut est `false`. Si `true`, empêche une application installée en cours de démarrage en cliquant sur l’URL ou en entrant l’URL dans Internet Explorer. Si le `install` attribut n’est pas présent, cet attribut est ignoré.|  
|`trustURLParameters`|facultatif. La valeur par défaut est `false`. Si `true`, permet à l’URL de contenir des paramètres de chaîne de requête qui sont passés dans l’application, bien comme arguments de ligne de commande sont passés à une application de ligne de commande. Pour plus d’informations, consultez [Guide pratique pour Récupérer les informations de chaîne de requête dans une application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si le `disallowUrlActivation` attribut est `true`, `trustUrlParameters` doit être exclu du manifeste, ou définie explicitement sur `false`.|  
  
 Le `deployment` élément contient également les éléments enfants suivants.  
  
## <a name="subscription"></a>subscription  
 facultatif. Contient le `update` élément. L’élément `subscription` ne comporte pas d’attributs. Si le `subscription` élément n’existe pas, le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application ne vérifie jamais les mises à jour. Si le `install` attribut de la `deployment` élément est `false`, le `subscription` élément est ignoré, car un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application always lancée à partir du réseau utilise la version la plus récente.  
  
## <a name="update"></a>update  
 Requis. Cet élément est un enfant de la `subscription` élément et contient le `beforeApplicationStartup` ou `expiration` élément. `beforeApplicationStartup` et `expiration` ne peut pas être spécifiés dans le même manifeste de déploiement.  
  
 L’élément `update` ne comporte pas d’attributs.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 facultatif. Cet élément est un enfant de le `update` élément et n’a aucun attribut. Lorsque le `beforeApplicationStartup` élément existe, l’application sera bloqué quand [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vérifie les mises à jour, si le client est en ligne. Si cet élément n’existe pas, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] commence par vérifier les mises à jour selon les valeurs spécifiées pour le `expiration` élément. `beforeApplicationStartup` et `expiration` ne peut pas être spécifiés dans le même manifeste de déploiement.  
  
## <a name="expiration"></a>expiration  
 facultatif. Cet élément est un enfant de le `update` élément, et n’a pas d’enfants. `beforeApplicationStartup` et `expiration` ne peut pas être spécifiés dans le même manifeste de déploiement. Lorsque la vérification de mise à jour se produit et une version mise à jour est détectée, la nouvelle version met en cache pendant l’exécution de la version existante. La nouvelle version s’installe ensuite au prochain lancement de le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
 Le `expiration` élément prend en charge les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maximumAge`|Requis. Identifie l’ancienneté la mise à jour en cours doit-il faire avant que l’application effectue une vérification de mise à jour. L’unité de temps est déterminée par la `unit` attribut.|  
|`unit`|Requis. Identifie l’unité de temps pour `maximumAge`. Les unités valides sont `hours`, `days`, et `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Pour le .NET Framework 2.0, cet élément est requis si le manifeste de déploiement contient un `subscription` section. Pour le .NET Framework 3.5 et versions ultérieures, cet élément est facultatif et par défaut sera le serveur et le chemin d’accès du fichier dans lequel le manifeste de déploiement a été découvert.  
  
 Cet élément est un enfant de l’élément `deployment` et contient l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`codebase`|Requis. Identifie l’emplacement, comme un identificateur URI (Uniform Resource), du manifeste de déploiement qui est utilisé pour mettre à jour le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Cet élément permet également de transférer les emplacements de mise à jour pour les installations basées sur CD. Doit être un URI valide.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez configurer votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application pour rechercher les mises à jour au démarrage, vérifier les mises à jour après le démarrage ou ne jamais rechercher des mises à jour. Pour rechercher les mises à jour au démarrage, vérifiez que le `beforeApplicationStartup` élément existe sous le `update` élément. Pour rechercher les mises à jour après le démarrage, vérifiez que le `expiration` élément existe sous le `update` élément, et que les intervalles de mise à jour sont fournies.  
  
 Pour désactiver la vérification des mises à jour, supprimer le `subscription` élément. Lorsque vous spécifiez dans le manifeste de déploiement pour ne jamais vérifier les mises à jour, vous pouvez vérifier manuellement les mises à jour à l’aide de la <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> (méthode).  
  
 Pour plus d’informations sur la façon dont deploymentProvider est lié aux mises à jour, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple de code suivant illustre un `deployment` élément dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste de déploiement. L’exemple utilise un `deploymentProvider` élément pour indiquer l’emplacement par défaut de mise à jour.  
  
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
