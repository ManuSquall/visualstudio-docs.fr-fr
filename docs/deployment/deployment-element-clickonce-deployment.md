---
title: "&lt;deployment&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> element [ClickOnce deployment manifest]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# &lt;deployment&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie les attributs utilisés pour le déploiement de mises à jour et l'exposition au système.  
  
## Syntaxe  
  
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
  
## Éléments et attributs  
 L'élément `deployment` est obligatoire et se trouve dans l'espace de noms `urn:schemas-microsoft-com:asm.v1`.  L'élément possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`install`|Obligatoire.  Spécifie si cette application définit une présence dans le menu **Démarrer** et dans l'application **Ajout\/Suppression de programmes** du panneau de configuration.  Les valeurs valides sont `true` et `false`.  Si la valeur est `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exécutera toujours la version la plus récente de cette application à partir du réseau et ne reconnaîtra pas l'élément `subscription`.|  
|`minimumRequiredVersion`|Facultatif.  Spécifie la version minimale de cette application en mesure de s'exécuter sur le client.  Si le numéro de version de l'application est inférieur au numéro de version fourni dans le manifeste de déploiement, l'application ne s'exécute pas.  Les numéros de version doivent être au format `N.N.N.N`, `N` représentant un entier non signé.  Si l'attribut `install` a la valeur `false`, `minimumRequiredVersion` ne doit pas être défini.|  
|`mapFileExtensions`|Facultatif.  Les valeurs par défaut ont la valeur `false`.  Si `vrai`, tous les fichiers dans le déploiement doivent avoir une extension .deploy.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supprimera cette extension de ces fichiers après téléchargement à partir du serveur Web.  Si vous publiez votre application à l'aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il ajoute automatiquement cette extension à tous les fichiers.  Ce paramètre autorise tous les fichiers dans un déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à être téléchargés à partir d'un serveur Web qui bloque la transmission des fichiers se terminant par des extensions « non sécurisées », telles que .exe.|  
|`disallowUrlActivation`|Facultatif.  Les valeurs par défaut ont la valeur `false`.  Si la valeur est `true`, empêche une application installée de démarrer lorsque l'utilisateur clique sur l'URL ou entre l'URL dans Internet Explorer.  Si l'attribut `install` n'est pas présent, cet attribut est ignoré.|  
|`trustURLParameters`|Facultatif.  Les valeurs par défaut ont la valeur `false`.  Si la valeur est `true`, permet à l'URL de contenir des paramètres de la chaîne de requête qui sont passés dans l'application, tout comme des arguments de ligne de commande sont passés à une application en mode ligne de commande.  Pour plus d'informations, consultez [Comment : récupérer les informations de chaîne de requête dans une application ClickOnce en ligne](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).<br /><br /> Si l'attribut `disallowUrlActivation` a la valeur `true`, `trustUrlParameters` doit être exclu du manifeste ou explicitement défini sur la valeur `false`.|  
  
 L'élément `deployment` contient également les éléments enfants suivants.  
  
## abonnement  
 Facultatif.  Contient l'élément `update`.  L'élément `subscription` ne contient pas d'attributs.  Si l'élément `subscription` n'existe pas, l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne vérifie jamais l'existence de mises à jour.  Si l'attribut `install` de l'élément `deployment` a la valeur `false`, l'élément `subscription` est ignoré dans la mesure où une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lancée à partir du réseau utilise toujours la version la plus récente.  
  
## update  
 Obligatoire.  Cet élément est un enfant de l'élément `subscription` et contient l'élément `beforeApplicationStartup` ou `expiration`.  `beforeApplicationStartup` et `expiration` ne peuvent pas être spécifiées à la fois dans le même manifeste de déploiement.  
  
 L'élément `update` ne contient pas d'attributs.  
  
## beforeApplicationStartup  
 Facultatif.  Cet élément est un enfant de l'élément `update` et ne possède pas d'attributs.  Lorsque l'élément `beforeApplicationStartup` existe, l'application est bloquée lorsque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vérifie les mises à jour, si le client est en ligne.  Si cet élément n'existe pas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] recherchera en premier des mises à jour selon les valeurs spécifiées pour l'élément `expiration`.  `beforeApplicationStartup` et `expiration` ne peuvent pas être spécifiées à la fois dans le même manifeste de déploiement.  
  
## expiration  
 Facultatif.  Cet élément est un enfant de l'élément `update`, et ne possède pas d'enfants.  `beforeApplicationStartup` et `expiration` ne peuvent pas être spécifiées à la fois dans le même manifeste de déploiement.  Lorsque la vérification des mises à jour se produit et qu'une version mise à jour est détectée, la nouvelle version se met en cache pendant l'exécution de la version existante.  La nouvelle version s'installe ensuite au prochain lancement de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 L'élément `expiration` prend en charge les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`maximumAge`|Obligatoire.  Détermine l'âge que doit avoir la mise à jour actuelle pour que l'application exécute une vérification de mise à jour.  L'unité de temps est déterminée par l'attribut `unit`.|  
|`unit`|Obligatoire.  Identifie l'unité de temps utilisée pour `maximumAge`.  Les unités valides sont `hours` \(heures\), `days` \(jours\) et `weeks` \(semaines\).|  
  
## deploymentProvider  
 Pour .NET Framework 2.0, cet élément est obligatoire si le manifeste de déploiement contient une section `subscription`.  Pour la version 3.5 du .NET Framework et les versions ultérieures, cet élément est facultatif et aura comme valeur par défaut le chemin d'accès du serveur et du fichier où le manifeste de déploiement a été trouvé.  
  
 Cet élément est un enfant de l'élément `deployment` et possède l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`codebase`|Obligatoire.  Identifie l'emplacement, sous la forme d'un identificateur URI \(Uniform Resource Identifier\), du manifeste de déploiement utilisé pour mettre à jour l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet élément permet également de transférer les emplacements de mise à jour pour les installations réalisées à partir de CD.  Doit être un URI valide.|  
  
## Notes  
 Vous pouvez configurer votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour vérifier les mises à jour au démarrage, vérifier les mises à jour après le démarrage ou ne jamais vérifier les mises à jour.  Pour vérifier les mises à jour au démarrage, assurez\-vous que l'élément `beforeApplicationStartup` existe sous l'élément `update`.  Pour vérifier les mises à jour après le démarrage, assurez\-vous que l'élément `expiration` existe sous l'élément `update` et que les intervalles de mise à jour requis sont indiqués.  
  
 Pour désactiver la vérification des mises à jour, supprimez l'élément `subscription`.  Lorsque vous spécifiez, dans le manifeste de déploiement, de ne jamais vérifier les mises à jour, vous pouvez néanmoins vérifier manuellement la présence de mises à jour à l'aide de la méthode <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>.  
  
 Pour plus d'informations sur la façon dont le deploymentProvider est en rapport avec les mises à jour, consultez [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## Exemples  
 L'exemple de code suivant illustre un élément `deployment` dans un manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'exemple utilise un élément `deploymentProvider` pour indiquer l'emplacement de mise à jour par défaut.  
  
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
  
## Voir aussi  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)