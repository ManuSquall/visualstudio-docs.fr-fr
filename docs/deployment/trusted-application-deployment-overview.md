---
title: Trusted Application Deployment Overview | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d4339295c47ee6bc8915eecfb581d9a0e8a4bed
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747668"
---
# <a name="trusted-application-deployment-overview"></a>Vue d’ensemble du déploiement d’applications approuvées
Cette rubrique offre une vue d’ensemble du déploiement d’applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui ont des autorisations élevées à l’aide de la technologie de déploiement d’applications approuvées.

 Le déploiement d'applications approuvées, qui fait partie de la technologie de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , permet aux entreprises de toute taille d'accorder des autorisations supplémentaires à une application managée de façon plus sûre et plus sécurisée, sans la confirmation de l'utilisateur. Avec le déploiement d'applications approuvées, une organisation peut simplement configurer un ordinateur client pour avoir une liste d'éditeurs approuvés, identifiés à l'aide de certificats Authenticode. Dès lors, toute application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] signée par un de ces éditeurs approuvés reçoit un niveau de confiance supérieur.

> [!NOTE]
> Le déploiement d'applications approuvées requiert une configuration unique de l'ordinateur d'un utilisateur. Dans les environnements de postes de travail gérés, cette configuration peut être effectuée à l'aide de la stratégie globale. Si ce n'est pas ce que vous voulez pour votre application, utilisez plutôt l'élévation d'autorisations. Pour plus d’informations, consultez [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="trusted-application-deployment-basics"></a>Concepts de base du déploiement d’applications approuvées
 Le tableau suivant indique les objets et les rôles qui interviennent dans le déploiement d'applications approuvées.

|Objet ou rôle|Description|
|--------------------|-----------------|
|administrateur|Entité organisationnelle responsable de la mise à jour et la maintenance des ordinateurs client|
|gestionnaire de confiance|Sous-système dans le Common Language Runtime (CLR) chargé d'appliquer la sécurité des applications clientes.|
|publisher|Entité qui écrit et gère l'application.|
|système de déploiement|Entité qui assemble et distribue l'application aux utilisateurs.|
|certificat|Signature de chiffrement qui se compose d'une clé publique et privée, émise en général par une autorité de certification (CA) pouvant se porter garante de son authenticité.|
|certificat Authenticode|Certificat avec des métadonnées incorporées décrivant, entre autres choses, les utilisations pour lesquelles le certificat peut être employé.|
|autorité de certification|Organisation qui vérifie l'identité des éditeurs et leur délivre des certificats incorporés avec les métadonnées de l'éditeur.|
|autorité racine|Autorité de certification qui autorise d'autres autorités de certification à émettre des certificats.|
|conteneur de clé|Espace de stockage logique dans Microsoft Windows pour stocker des certificats.|
|éditeur approuvé|Éditeur dont le certificat Authenticode a été ajouté à une liste de certificats de confiance (CTL) sur un ordinateur client.|

 Dans les grandes entreprises, l'éditeur et le système de déploiement sont souvent deux entités distinctes :

- L'éditeur est le groupe qui crée l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

- Le système de déploiement est le groupe, en général le service informatique, qui distribue l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aux ordinateurs de bureau de l'entreprise.

Vous devez suivre ces étapes pour tirer parti du déploiement d'applications approuvées :

1. Obtenir un certificat pour l'éditeur.

2. Ajouter l'éditeur au magasin d'éditeurs approuvés sur tous les clients.

3. Créer votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

4. Signer le manifeste de déploiement avec le certificat de l'éditeur.

5. Publier le déploiement d'applications sur les ordinateurs clients.

### <a name="obtain-a-certificate-for-the-publisher"></a>Obtenir un certificat pour l’éditeur
 Les certificats numériques sont un composant principal du système de sécurité et d'authentification de Microsoft Authenticode. Authenticode est un composant standard du système d'exploitation Windows. Toutes les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] doivent être signées avec un certificat numérique, qu'elles participent ou non au déploiement d'applications approuvées. Pour obtenir une explication complète du fonctionne d’Authenticode avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md).

### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Ajouter l’éditeur au magasin d’éditeurs approuvés
 Pour que votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] reçoive un niveau supérieur de confiance, vous devez ajouter votre certificat en tant qu'éditeur approuvé à chaque ordinateur client sur lequel l'application s'exécutera. Cette tâche est une configuration unique. Une fois terminée, vous pouvez déployer autant d'applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] signées avec le certificat de votre éditeur que vous souhaitez, et elles s'exécuteront toutes avec un niveau de confiance élevé.

 Si vous déployez votre application dans un environnement de bureau géré, par exemple, un intranet d'entreprise exécutant le système d'exploitation Windows, vous pouvez ajouter des éditeurs approuvés au magasin d'un client en créant une nouvelle liste de certificats de confiance (CTL) avec la stratégie de groupe. Pour plus d’informations, consultez [Créer une liste de certificats de confiance pour un objet Stratégie de groupe](http://go.microsoft.com/fwlink/?LinkId=102576).

 Si vous ne déployez pas votre application dans un environnement de bureau géré, vous disposez des options suivantes pour ajouter un certificat au magasin d'éditeurs approuvés :

- Espace de noms <xref:System.Security.Cryptography?displayProperty=fullName> .

- *CertMgr.exe*, qui est un composant d’Internet Explorer et qui existe donc sur Windows 98 et toutes les versions ultérieures. Pour plus d’informations, consultez [Certmgr.exe (outil de gestionnaire de certificats)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).

### <a name="create-a-clickonce-application"></a>Créer une application ClickOnce
 Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est une application de client .NET Framework combinée avec des fichiers manifestes qui décrivent l’application et fournissent les paramètres d’installation. Vous pouvez transformer votre programme en application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de la commande **Publier** dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également générer tous les fichiers requis pour le déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide des outils inclus dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Pour obtenir des instructions détaillées sur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement, consultez [procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

 Le déploiement d'applications approuvées est spécifique de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]et peut uniquement être utilisé avec des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

### <a name="sign-the-deployment"></a>Signer le déploiement
 Après avoir obtenu votre certificat, vous devez l'utiliser pour signer votre déploiement. Si vous déployez votre application à l'aide de l'Assistant Publication de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ce dernier génère automatiquement un certificat de test pour vous si vous n'avez pas spécifié de certificat. Vous pouvez également utiliser la fenêtre du Concepteur de projets [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , pour fournir un certificat fourni par une autorité de certification.  Voir également [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!CAUTION]
> Nous ne recommandons pas le déploiement de l'application avec un certificat de test.

 Vous pouvez également signer l’application à l’aide des outils *Mage.exe* ou *MageUI.exe* du SDK. Pour plus d’informations, consultez [Procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pour obtenir une liste complète des options de ligne de commande relatives à la signature de déploiement, consultez [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

### <a name="publish-the-application"></a>Publier l’application
 Dès que vous avez signé vos manifestes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , l'application est prête à être publiée dans votre emplacement d'installation. L'emplacement d'installation peut être un serveur web, un partage de fichiers ou le disque local. Quand un client accède au manifeste de déploiement pour la première fois, le Gestionnaire de confiance doit déterminer si l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a été autorisée ou non à ne pas s'exécuter à un niveau de confiance supérieur par un éditeur approuvé installé. Le Gestionnaire de confiance fait ce choix en comparant le certificat utilisé pour signer le déploiement aux certificats stockés dans le magasin d'éditeurs approuvés du client. Si le Gestionnaire de confiance trouve une correspondance, l'application s'exécute avec un niveau de confiance élevé.

## <a name="trusted-application-deployment-and-permission-elevation"></a>Déploiement d'applications approuvées et élévation d'autorisations
 Si l'éditeur actuel n'est pas un éditeur approuvé, le Gestionnaire de confiance utilise l'élévation d'autorisations pour demander à l'utilisateur s'il souhaite accorder à votre application des autorisations élevées. Toutefois, si l'élévation d'autorisations est désactivée par l'administrateur, l'application ne peut pas obtenir l'autorisation de s'exécuter. L'application ne s'exécute pas et aucune notification n'est affichée à l'utilisateur. Pour plus d’informations sur l’élévation d’autorisations, consultez [sécurisation des Applications ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="limitations-of-trusted-application-deployment"></a>Limitations du déploiement d'applications approuvées
 Vous pouvez utiliser le déploiement d'applications approuvées pour accorder une confiance élevée aux applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déployées sur le web ou via un partage de fichiers d'entreprise. Vous n'êtes pas obligé d'utiliser le déploiement d'applications approuvées pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuées sur un CD, car, par défaut, ces applications ont un niveau de confiance totale.

## <a name="see-also"></a>Voir aussi
- [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
