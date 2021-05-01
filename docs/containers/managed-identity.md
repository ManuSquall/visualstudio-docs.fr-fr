---
title: Utilisation d’une identité gérée avec Bridge pour Kubernetes
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Découvrez comment utiliser l’identité gérée Azure Active Directory (Azure AD) dans un cluster AKS avec Bridge vers Kubernetes
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335090"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Utilisation d’une identité gérée avec Bridge vers Kubernetes

Si votre cluster AKS utilise les fonctionnalités de sécurité des [identités gérées](/azure/active-directory/managed-identities-azure-resources/overview) pour sécuriser l’accès aux secrets et aux ressources, Bridge to Kubernetes a besoin d’une configuration spéciale pour s’assurer qu’il peut fonctionner avec ces fonctionnalités. Un jeton Azure Active Directory (AD) doit être téléchargé sur l’ordinateur local pour garantir que l’exécution et le débogage locales sont correctement sécurisés, ce qui nécessite une configuration spéciale dans Bridge pour Kubernetes. Cet article explique comment configurer Bridge vers Kubernetes pour travailler avec des services qui utilisent une identité gérée.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>Comment configurer votre service pour utiliser une identité gérée

Pour activer un ordinateur local avec prise en charge de l’identité managée, dans le fichier *KubernetesLocalConfig. YAML* , dans la `enableFeatures` section, ajoutez `ManagedIdentity` . Ajoutez la `enableFeatures` section si elle ne s’y trouve pas déjà.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Veillez à utiliser uniquement l’identité gérée pour Bridge vers Kubernetes quand vous travaillez avec des clusters de développement, et non des clusters de production, car le jeton Azure AD est extrait sur l’ordinateur local, ce qui présente un risque potentiel pour la sécurité.

Si vous n’avez pas de fichier *KubernetesLocalConfig. YAML* , vous pouvez en créer un. consultez [Comment : configurer Bridge vers Kubernetes](configure-bridge-to-kubernetes.md).

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Comment récupérer les jetons de Azure Active Directory

Vous devez vous assurer que vous vous fiez à <xref:Azure.Identity.DefaultAzureCredential> ou <xref:Azure.Identity.ManagedIdentityCredential> dans le code lors de l’extraction du jeton.

Le code C# suivant montre comment récupérer des informations d’identification de compte de stockage lorsque vous utilisez `ManagedIdentityCredential` :

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Le code suivant montre comment récupérer des informations d’identification de compte de stockage lorsque vous utilisez DefaultAzureCredential :

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Pour savoir comment accéder à d’autres ressources Azure à l’aide de Managed Identity, consultez la section [étapes suivantes](#next-steps) .

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>Recevoir des alertes Azure quand des jetons sont téléchargés

Chaque fois que vous utilisez Bridge pour Kubernetes sur un service, le jeton Azure AD est téléchargé sur l’ordinateur local. Vous pouvez autoriser les alertes Azure à être averti lorsque cela se produit. Pour plus d’informations, consultez [activer Azure Defender](/azure/security-center/enable-azure-defender). N’oubliez pas qu’il y a un frais (après une période d’essai de 30 jours).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez configuré Bridge sur Kubernetes pour qu’il fonctionne avec votre cluster AKS qui utilise une identité gérée, vous pouvez effectuer un débogage normal. Consultez [Bridge-to-kubernetes. MD # Connect-to-your-cluster-and-Debug-a-service].

Pour en savoir plus sur l’utilisation de Managed identifier pour accéder aux ressources Azure, suivez les didacticiels suivants :

- [Didacticiel : Utiliser une identité managée affectée par le système de machine virtuelle Linux pour accéder au Stockage Azure](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [Didacticiel : Utiliser une identité managée attribuée par le système de la machine virtuelle Linux pour accéder à Azure Data Lake Store](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [Tutoriel : Utiliser une identité managée de machine virtuelle Linux attribuée par le système pour accéder à Azure Key Vault](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

Il existe également d’autres didacticiels dans cette section pour l’utilisation de l’identité gérée pour accéder à d’autres ressources Azure.

## <a name="see-also"></a>Voir aussi

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
