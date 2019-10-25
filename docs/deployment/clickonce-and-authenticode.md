---
title: ClickOnce et Authenticode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0920da406e911f388c2b9ae77db16ee325aaae65
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806978"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce et Authenticode
*Authenticode* est une technologie Microsoft qui utilise le chiffrement standard pour signer le code d’application avec des certificats numériques. Ces certificats permettent de vérifier l’authenticité de l’éditeur de l’application. En utilisant Authenticode pour le déploiement d’applications, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] réduit le risque d’un cheval de Troie. Un cheval de Troie est un virus ou autre programme dangereux qu’un tiers malveillant présente comme un programme légitime provenant d’une source de confiance connue. La signature des déploiements [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] avec un certificat numérique est une étape facultative permettant de vérifier que les assemblys et les fichiers ne sont pas falsifiés.

 Les sections suivantes décrivent les différents types de certificats numériques utilisés avec Authenticode, la validation des certificats à l’aide d’autorités de certification (CA), le rôle de l’horodatage dans les certificats et les méthodes de stockage possibles pour les certificats.

## <a name="authenticode-and-code-signing"></a>Authenticode et signature de code
 Un *certificat numérique* est un fichier qui contient une paire de clés publique/privée de chiffrement, ainsi que des métadonnées décrivant l’éditeur à qui le certificat a été délivré et l’agence qui a publié le certificat.

 Il existe différents types de certificats Authenticode. Chacun d’eux est configuré pour un type de signature particulier. Pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , vous devez disposer d’un certificat Authenticode valide pour la signature de code. Si vous tentez de signer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] avec un autre type de certificat, tel qu’un certificat numérique par e-mail, cela ne fonctionne pas. Pour plus d’informations, consultez [Introduction to Code Signing](/windows/desktop/seccrypto/cryptography-tools).

 Vous pouvez obtenir un certificat pour la signature de code de trois façons différentes :

- Achetez un certificat à un fournisseur de certificats.

- Procurez-vous un certificat auprès d’un groupe de votre organisation responsable de la création de certificats numériques.

- Générez votre propre certificat à l’aide de l’applet de commande PowerShell New-SelfSignedCertificate ou à l’aide de *Makecert. exe*, qui est inclus dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].

### <a name="how-using-certificate-authorities-helps-users"></a>Avantages de l’utilisation d’autorités de certification pour les utilisateurs
 Un certificat généré à l’aide de New-SelfSignedCertificate ou *MakeCert.exe* utilitaire est généralement appelé un *self-cert* ou un *certificat de test*. Ce type de certificat fonctionne quasiment de la même façon qu’un fichier *.snk* dans le .NET Framework. Il se compose uniquement d’une paire de clés publique/privée de chiffrement et ne contient aucune information vérifiable concernant l’éditeur. Vous pouvez utiliser des certificats automatiques pour déployer des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] très fiables sur un intranet. Toutefois, quand ces applications sont exécutées sur un ordinateur client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les identifie comme provenant d’un éditeur inconnu. Par défaut, les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] signées avec des certificats automatiques et déployées sur Internet ne peuvent pas utiliser le déploiement d’applications approuvées.

 En revanche, si vous recevez un certificat d’une autorité de certification, par exemple un fournisseur de certificats ou un service de votre entreprise, le certificat offre davantage de sécurité pour vos utilisateurs. Non seulement il identifie l’éditeur du logiciel signé, mais il vérifie aussi cette identité auprès de l’autorité de certification qui l’a signé. Si l’autorité de certification n’est pas l’autorité racine, Authenticode remonte également jusqu’à l’autorité racine pour vérifier que l’autorité de certification est autorisée à publier des certificats. Pour garantir une sécurité optimale, utilisez un certificat publié par une autorité de certification quand cela est possible.

 Pour plus d’informations sur la génération de certificats automatiques, consultez [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) ou [Makecert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Horodatages
 Les certificats utilisés pour signer des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] expirent après une certaine durée (douze mois, le plus souvent). Pour éviter aux utilisateurs d’avoir à resigner constamment les applications avec de nouveaux certificats, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prend en charge l’horodatage. Quand une application est signée avec un horodatage, son certificat est accepté même s’il a expiré, à condition que l’horodatage soit valide. Cela permet de télécharger et d’exécuter des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui ont des certificats arrivés à expiration, mais des horodatages valides. Cela permet également aux applications installées qui ont des certificats expirés de continuer à télécharger et installer les mises à jour.

 Pour inclure un horodatage dans un serveur d’applications, un serveur d’horodatage doit être disponible. Pour plus d’informations sur la sélection d’un serveur d’horodatage, consultez [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Mettre à jour les certificats expirés
 Dans les versions antérieures du .NET Framework, la mise à jour d’une application dont le certificat a expiré peut empêcher cette application de fonctionner. Pour résoudre ce problème, utilisez l’une des méthodes suivantes :

- Mettez à jour .NET Framework vers la version 2.0 SP1 ou ultérieure sur Windows XP, ou la version 3.5 ou ultérieure sur Windows Vista.

- Désinstallez l’application, puis réinstallez une nouvelle version avec un certificat valide.

- Créez un assembly de ligne de commande qui met à jour le certificat. Pour obtenir des informations détaillées sur ce processus, consultez l’ [article 925521 du support Microsoft](https://support.microsoft.com/help/925521).

### <a name="store-certificates"></a>Stocker des certificats

- Vous pouvez stocker les certificats dans un fichier *.pfx* sur votre système de fichiers ou les stocker dans un conteneur de clé. Un utilisateur d’un domaine Windows peut avoir un ou plusieurs conteneurs de clé. Par défaut, *MakeCert.exe* stocke les certificats dans votre conteneur de clé personnel, sauf si vous spécifiez qu’il doit les enregistrer dans un fichier *.pfx*. *Mage.exe* et *MageUI.exe*, les outils du [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] pour la création de déploiements [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous permettent d’utiliser des certificats stockés à l’aide de l’une ou l’autre de ces méthodes.

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
