---
title: "Vue d&#39;ensemble du d&#233;ploiement d&#39;applications approuv&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déploiement ClickOnce, installation sans demande de confirmation"
  - "Déploiement ClickOnce (sécurité)"
  - "déploiement d'applications approuvées"
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vue d&#39;ensemble du d&#233;ploiement d&#39;applications approuv&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique offre une vue d’ensemble du déploiement d’applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui ont des autorisations élevées à l’aide de la technologie de déploiement d’applications approuvées.  
  
 Le déploiement d'applications approuvées, qui fait partie de la technologie de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], permet aux entreprises de toute taille d'accorder des autorisations supplémentaires à une application managée de façon plus sûre et plus sécurisée, sans la confirmation de l'utilisateur. Avec le déploiement d'applications approuvées, une organisation peut simplement configurer un ordinateur client pour avoir une liste d'éditeurs approuvés, identifiés à l'aide de certificats Authenticode. Dès lors, toute application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] signée par un de ces éditeurs approuvés reçoit un niveau de confiance supérieur.  
  
> [!NOTE]
>  Le déploiement d'applications approuvées requiert une configuration unique de l'ordinateur d'un utilisateur. Dans les environnements de postes de travail gérés, cette configuration peut être effectuée à l'aide de la stratégie globale. Si ce n'est pas ce que vous voulez pour votre application, utilisez plutôt l'élévation d'autorisations. Pour plus d'informations, consultez [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Concepts de base du déploiement d'applications approuvées  
 Le tableau suivant indique les objets et les rôles qui interviennent dans le déploiement d'applications approuvées.  
  
|Objet ou rôle|Description|  
|-------------------|-----------------|  
|administrateur|Entité organisationnelle responsable de la mise à jour et la maintenance des ordinateurs client|  
|gestionnaire de confiance|Sous\-système dans le Common Language Runtime \(CLR\) chargé d'appliquer la sécurité des applications clientes.|  
|publisher|Entité qui écrit et gère l'application.|  
|système de déploiement|Entité qui assemble et distribue l'application aux utilisateurs.|  
|certificat|Signature de chiffrement qui se compose d'une clé publique et privée, émise en général par une autorité de certification \(CA\) pouvant se porter garante de son authenticité.|  
|certificat Authenticode|Certificat avec des métadonnées incorporées décrivant, entre autres choses, les utilisations pour lesquelles le certificat peut être employé.|  
|autorité de certification|Organisation qui vérifie l'identité des éditeurs et leur délivre des certificats incorporés avec les métadonnées de l'éditeur.|  
|autorité racine|Autorité de certification qui autorise d'autres autorités de certification à émettre des certificats.|  
|conteneur de clé|Espace de stockage logique dans Microsoft Windows pour stocker des certificats.|  
|éditeur approuvé|Éditeur dont le certificat Authenticode a été ajouté à une liste de certificats de confiance \(CTL\) sur un ordinateur client.|  
  
 Dans les grandes entreprises, l'éditeur et le système de déploiement sont souvent deux entités distinctes :  
  
-   L'éditeur est le groupe qui crée l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
-   Le système de déploiement est le groupe, en général le service informatique, qui distribue l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aux ordinateurs de bureau de l'entreprise.  
  
 Vous devez suivre ces étapes pour tirer parti du déploiement d'applications approuvées :  
  
1.  Obtenir un certificat pour l'éditeur.  
  
2.  Ajouter l'éditeur au magasin d'éditeurs approuvés sur tous les clients.  
  
3.  Créer votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
4.  Signer le manifeste de déploiement avec le certificat de l'éditeur.  
  
5.  Publier le déploiement d'applications sur les ordinateurs clients.  
  
### Obtenir un certificat pour l'éditeur  
 Les certificats numériques sont un composant principal du système de sécurité et d'authentification de Microsoft Authenticode. Authenticode est un composant standard du système d'exploitation Windows. Toutes les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] doivent être signées avec un certificat numérique, qu'elles participent ou non au déploiement d'applications approuvées. Pour obtenir une explication complète du fonctionnement d’Authenticode avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### Ajouter l'éditeur au magasin d'éditeurs approuvés  
 Pour que votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] reçoive un niveau supérieur de confiance, vous devez ajouter votre certificat en tant qu'éditeur approuvé à chaque ordinateur client sur lequel l'application s'exécutera. Cette tâche est une configuration unique. Une fois terminée, vous pouvez déployer autant d'applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] signées avec le certificat de votre éditeur que vous souhaitez, et elles s'exécuteront toutes avec un niveau de confiance élevé.  
  
 Si vous déployez votre application dans un environnement de bureau géré, par exemple, un intranet d'entreprise exécutant le système d'exploitation Windows, vous pouvez ajouter des éditeurs approuvés au magasin d'un client en créant une nouvelle liste de certificats de confiance \(CTL\) avec la stratégie de groupe. Pour plus d’informations, consultez [Créer une liste de certificats de confiance pour un objet Stratégie de groupe](http://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Si vous ne déployez pas votre application dans un environnement de bureau géré, vous disposez des options suivantes pour ajouter un certificat au magasin d'éditeurs approuvés :  
  
-   Espace de noms <xref:System.Security.Cryptography?displayProperty=fullName>.  
  
-   CertMgr.exe, composant d'Internet Explorer qui, par conséquent, existe sur Windows 98 et toutes les versions ultérieures. Pour plus d'informations, consultez [Certmgr.exe \(Certificate Manager Tool\)](../Topic/Certmgr.exe%20\(Certificate%20Manager%20Tool\).md).  
  
### Créer une application ClickOnce  
 Une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est une application cliente [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] combinée avec des fichiers manifestes qui décrivent l'application et fournissent les paramètres d'installation. Vous pouvez transformer votre programme en application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de la commande **Publier** dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également générer tous les fichiers requis pour le déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide des outils inclus dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Pour obtenir une procédure pas à pas du déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Le déploiement d'applications approuvées est spécifique de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et peut uniquement être utilisé avec des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Signer le déploiement  
 Après avoir obtenu votre certificat, vous devez l'utiliser pour signer votre déploiement. Si vous déployez votre application à l'aide de l'Assistant Publication de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ce dernier génère automatiquement un certificat de test pour vous si vous n'avez pas spécifié de certificat. Vous pouvez également utiliser la fenêtre du Concepteur de projets [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], pour fournir un certificat fourni par une autorité de certification.  Consultez également [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) ou [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)).  
  
> [!CAUTION]
>  Nous ne recommandons pas le déploiement de l'application avec un certificat de test.  
  
 Vous pouvez également signer l'application à l'aide des outils des SDK Mage.exe ou MageUI.exe. Pour plus d'informations, consultez [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pour obtenir une liste complète des options de ligne de commande relatives à la signature de déploiement, consultez [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
### Publier l'application  
 Dès que vous avez signé vos manifestes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], l'application est prête à être publiée dans votre emplacement d'installation. L'emplacement d'installation peut être un serveur web, un partage de fichiers ou le disque local. Quand un client accède au manifeste de déploiement pour la première fois, le Gestionnaire de confiance doit déterminer si l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a été autorisée ou non à ne pas s'exécuter à un niveau de confiance supérieur par un éditeur approuvé installé. Le Gestionnaire de confiance fait ce choix en comparant le certificat utilisé pour signer le déploiement aux certificats stockés dans le magasin d'éditeurs approuvés du client. Si le Gestionnaire de confiance trouve une correspondance, l'application s'exécute avec un niveau de confiance élevé.  
  
## Déploiement d'applications approuvées et élévation d'autorisations  
 Si l'éditeur actuel n'est pas un éditeur approuvé, le Gestionnaire de confiance utilise l'élévation d'autorisations pour demander à l'utilisateur s'il souhaite accorder à votre application des autorisations élevées. Toutefois, si l'élévation d'autorisations est désactivée par l'administrateur, l'application ne peut pas obtenir l'autorisation de s'exécuter. L'application ne s'exécute pas et aucune notification n'est affichée à l'utilisateur. Pour plus d’informations sur l’élévation d’autorisations, consultez [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Limitations du déploiement d'applications approuvées  
 Vous pouvez utiliser le déploiement d'applications approuvées pour accorder une confiance élevée aux applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déployées sur le web ou via un partage de fichiers d'entreprise. Vous n'êtes pas obligé d'utiliser le déploiement d'applications approuvées pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuées sur un CD, car, par défaut, ces applications ont un niveau de confiance totale.  
  
## Voir aussi  
 [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)