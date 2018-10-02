---
title: ClickOnce et Authenticode | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: cf05c73ee621d9eda1619627b2d0b65611e447fd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507138"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce et Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [ClickOnce et Authenticode](https://docs.microsoft.com/visualstudio/deployment/clickonce-and-authenticode).  
  
Authenticode * est une technologie Microsoft qui utilise le chiffrement standard pour signer le code d’application avec des certificats numériques qui vérifient l’authenticité du serveur de publication de l’application. En utilisant Authenticode pour le déploiement d’applications, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] réduit le risque d’un cheval de Troie. Un cheval de Troie est un virus ou autre programme dangereux qu’un tiers malveillant présente comme un programme légitime provenant d’une source de confiance connue. La signature des déploiements [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] avec un certificat numérique est une étape facultative permettant de vérifier que les assemblys et les fichiers ne sont pas falsifiés.  
  
 Les sections suivantes décrivent les différents types de certificats numériques utilisés avec Authenticode, la validation des certificats à l’aide d’autorités de certification (CA), le rôle de l’horodatage dans les certificats et les méthodes de stockage possibles pour les certificats.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode et signature de code  
 Un *certificat numérique* est un fichier qui contient une paire de clés publique/privée de chiffrement, ainsi que des métadonnées décrivant l’éditeur à qui le certificat a été délivré et l’agence qui a publié le certificat.  
  
 Il existe différents types de certificats Authenticode. Chacun d’eux est configuré pour un type de signature particulier. Pour les applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], vous devez disposer d’un certificat Authenticode valide pour la signature de code. Si vous tentez de signer un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application avec un autre type de certificat, tel qu’un certificat numérique par e-mail, il ne fonctionnera pas. Pour plus d’informations, consultez [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=179452)(Présentation de la signature de code).  
  
 Vous pouvez obtenir un certificat pour la signature de code de trois façons différentes :  
  
-   Achetez un certificat à un fournisseur de certificats.  
  
-   Procurez-vous un certificat auprès d’un groupe de votre organisation responsable de la création de certificats numériques.  
  
-   Générez votre propre certificat avec MakeCert.exe, fourni dans le [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Avantages de l’utilisation d’autorités de certification pour les utilisateurs  
 Un certificat généré à l’aide de l’utilitaire MakeCert.exe est généralement appelé *certificat automatique* ou *certificat de test*. Ce type de certificat fonctionne quasiment de la même façon qu’un fichier .snk dans le .NET Framework. Il se compose uniquement d’une paire de clés publique/privée de chiffrement et ne contient aucune information vérifiable concernant l’éditeur. Vous pouvez utiliser des certificats automatiques pour déployer des applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] très fiables sur un intranet. Toutefois, quand ces applications sont exécutées sur un ordinateur client, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] les identifie comme provenant d’un éditeur inconnu. Par défaut, les applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] signées avec des certificats automatiques et déployées sur Internet ne peuvent pas utiliser le déploiement d’applications approuvées.  
  
 En revanche, si vous recevez un certificat d’une autorité de certification, par exemple un fournisseur de certificats ou un service de votre entreprise, le certificat offre davantage de sécurité pour vos utilisateurs. Non seulement il identifie l’éditeur du logiciel signé, mais il vérifie aussi cette identité auprès de l’autorité de certification qui l’a signé. Si l’autorité de certification n’est pas l’autorité racine, Authenticode remonte également jusqu’à l’autorité racine pour vérifier que l’autorité de certification est autorisée à publier des certificats. Pour garantir une sécurité optimale, utilisez un certificat publié par une autorité de certification quand cela est possible.  
  
 Pour plus d’informations sur la génération de certificats automatiques, consultez [Makecert.exe (outil Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Horodatages  
 Les certificats utilisés pour signer des applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] expirent après une certaine durée (douze mois, le plus souvent). Pour éviter aux utilisateurs d’avoir à resigner constamment les applications avec de nouveaux certificats, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] prend en charge l’horodatage. Quand une application est signée avec un horodatage, son certificat est accepté même s’il a expiré, à condition que l’horodatage soit valide. Cela permet de télécharger et d’exécuter des applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] qui ont des certificats arrivés à expiration, mais des horodatages valides. Cela permet également aux applications installées qui ont des certificats expirés de continuer à télécharger et installer les mises à jour.  
  
 Pour inclure un horodatage dans un serveur d’applications, un serveur d’horodatage doit être disponible. Pour plus d’informations sur la sélection d’un serveur d’horodatage, consultez [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Mise à jour des certificats expirés  
 Dans les versions antérieures du .NET Framework, la mise à jour d’une application dont le certificat a expiré peut empêcher cette application de fonctionner. Pour résoudre ce problème, utilisez l’une des méthodes suivantes :  
  
-   Mettez à jour .NET Framework vers la version 2.0 SP1 ou ultérieure sur Windows XP, ou la version 3.5 ou ultérieure sur Windows Vista.  
  
-   Désinstallez l’application, puis réinstallez une nouvelle version avec un certificat valide.  
  
-   Créez un assembly de ligne de commande qui met à jour le certificat. Pour obtenir des informations détaillées sur ce processus, consultez l’ [article 925521 du support Microsoft](http://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="storing-certificates"></a>Stockage des certificats  
  
-   Vous pouvez stocker les certificats dans un fichier .pfx sur votre système de fichiers ou les stocker dans un conteneur de clé. Un utilisateur d’un domaine Windows peut avoir un ou plusieurs conteneurs de clé. Par défaut, MakeCert.exe stocke les certificats dans votre conteneur de clé personnel, sauf si vous spécifiez qu’il doit les enregistrer dans un fichier .pfx. Mage.exe et MageUI.exe, outils du [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] pour la création de déploiements [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], vous permettent d’utiliser des certificats stockés à l’aide de l’une ou l’autre de ces méthodes.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (outil Manifest Generation and Editing)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)



