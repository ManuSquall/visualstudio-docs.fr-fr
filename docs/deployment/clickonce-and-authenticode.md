---
title: ClickOnce et Authenticode (fr) Microsoft Docs
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
ms.openlocfilehash: b9b0e22f56ab68be521eda7a765a2be7e23bbf92
ms.sourcegitcommit: 6c3aa85ff17916936018d121e7a0d1b486f6c7eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093954"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce et Authenticode
*Authenticode* est une technologie Microsoft qui utilise le chiffrement standard pour signer le code d’application avec des certificats numériques. Ces certificats permettent de vérifier l’authenticité de l’éditeur de l’application. En utilisant Authenticode pour le déploiement d’applications, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] réduit le risque d’un cheval de Troie. Un cheval de Troie est un virus ou autre programme dangereux qu’un tiers malveillant présente comme un programme légitime provenant d’une source de confiance connue. La signature des déploiements [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] avec un certificat numérique est une étape facultative permettant de vérifier que les assemblys et les fichiers ne sont pas falsifiés.

 Les sections suivantes décrivent les différents types de certificats numériques utilisés avec Authenticode, la validation des certificats à l’aide d’autorités de certification (CA), le rôle de l’horodatage dans les certificats et les méthodes de stockage possibles pour les certificats.

## <a name="authenticode-and-code-signing"></a>Authenticode et signature de code
 Un *certificat numérique* est un fichier qui contient une paire de clés publique/privée de chiffrement, ainsi que des métadonnées décrivant l’éditeur à qui le certificat a été délivré et l’agence qui a publié le certificat.

 Il existe différents types de certificats Authenticode. Chacun d’eux est configuré pour un type de signature particulier. Pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , vous devez disposer d’un certificat Authenticode valide pour la signature de code. Si vous tentez de signer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] avec un autre type de certificat, tel qu’un certificat numérique par e-mail, cela ne fonctionne pas. Pour plus d’informations, voir [Introduction à la signature de code](/windows/desktop/seccrypto/cryptography-tools).

 Vous pouvez obtenir un certificat pour la signature de code de trois façons différentes :

- Achetez un certificat à un fournisseur de certificats.

- Procurez-vous un certificat auprès d’un groupe de votre organisation responsable de la création de certificats numériques.

- Générer votre propre certificat en utilisant le New-SelfSignedCertificate PowerShell cmdlet, ou en utilisant [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] *MakeCert.exe*, qui est inclus avec le .

### <a name="how-using-certificate-authorities-helps-users"></a>Avantages de l’utilisation d’autorités de certification pour les utilisateurs
 Un certificat généré à l’aide de New-SelfSignedCertificate ou *MakeCert.exe* utilitaire est généralement appelé un *self-cert* ou un *certificat de test*. Ce type de certificat fonctionne quasiment de la même façon qu’un fichier *.snk* dans le .NET Framework. Il se compose uniquement d’une paire de clés publique/privée de chiffrement et ne contient aucune information vérifiable concernant l’éditeur. Vous pouvez utiliser des certificats automatiques pour déployer des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] très fiables sur un intranet. Toutefois, quand ces applications sont exécutées sur un ordinateur client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les identifie comme provenant d’un éditeur inconnu. Par défaut, les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] signées avec des certificats automatiques et déployées sur Internet ne peuvent pas utiliser le déploiement d’applications approuvées.

 En revanche, si vous recevez un certificat d’une autorité de certification, par exemple un fournisseur de certificats ou un service de votre entreprise, le certificat offre davantage de sécurité pour vos utilisateurs. Non seulement il identifie l’éditeur du logiciel signé, mais il vérifie aussi cette identité auprès de l’autorité de certification qui l’a signé. Si l’autorité de certification n’est pas l’autorité racine, Authenticode remonte également jusqu’à l’autorité racine pour vérifier que l’autorité de certification est autorisée à publier des certificats. Pour garantir une sécurité optimale, utilisez un certificat publié par une autorité de certification quand cela est possible.

 Pour plus d’informations sur la génération d’auto-certificats, voir [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) ou [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Horodatages
 Les certificats utilisés pour signer des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] expirent après une certaine durée (douze mois, le plus souvent). Pour éviter aux utilisateurs d’avoir à resigner constamment les applications avec de nouveaux certificats, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prend en charge l’horodatage. Quand une application est signée avec un horodatage, son certificat est accepté même s’il a expiré, à condition que l’horodatage soit valide. Cela permet de télécharger et d’exécuter des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui ont des certificats arrivés à expiration, mais des horodatages valides. Cela permet également aux applications installées qui ont des certificats expirés de continuer à télécharger et installer les mises à jour.

 Pour inclure un horodatage dans un serveur d’applications, un serveur d’horodatage doit être disponible. Pour plus d’informations sur la sélection d’un serveur d’horodatage, consultez [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Mise à jour des certificats expirés
 Dans les versions antérieures du .NET Framework, la mise à jour d’une application dont le certificat a expiré peut empêcher cette application de fonctionner. Pour résoudre ce problème, utilisez l’une des méthodes suivantes :

- Mettez à jour .NET Framework vers la version 2.0 SP1 ou ultérieure sur Windows XP, ou la version 3.5 ou ultérieure sur Windows Vista.

- Désinstallez l’application, puis réinstallez une nouvelle version avec un certificat valide.

### <a name="store-certificates"></a>Certificats de magasin

- Vous pouvez stocker des certificats comme un fichier *.pfx* sur votre système de fichiers, ou vous pouvez les stocker à l’intérieur d’un conteneur clé. Un utilisateur d’un domaine Windows peut avoir un ou plusieurs conteneurs de clé. Par défaut, *MakeCert.exe* stockera des certificats dans votre conteneur de clé personnel, sauf si vous spécifiez qu’il devrait l’enregistrer à un *.pfx* à la place. *Mage.exe* et *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les outils de création de déploiements, vous permettent d’utiliser des certificats stockés de l’une ou l’autre manière.

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Applications ClickOnce sécurisées](../deployment/securing-clickonce-applications.md)
- [Aperçu du déploiement d’applications de confiance](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
