---
title: Informations de référence sur les API non managées ClickOnce | Microsoft Docs
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b536a17df4f54158aa6f157a0d9795cf359ddc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900270"
---
# <a name="clickonce-unmanaged-api-reference"></a>Informations de référence sur les API non managées ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API publiques non managées à partir de dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Nettoie ou désinstalle toutes les applications en ligne du cache d' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

### <a name="return-value"></a>Valeur retournée
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Notes
 L’appel de CleanOnlineAppCache démarre le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] service s’il n’est pas déjà en cours d’exécution.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Récupère les informations de déploiement à partir du manifeste et de l’URL d’activation.

### <a name="parameters"></a>Paramètres

|Paramètre|Description|Type|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Pointeur vers le `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Pointeur vers le `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Pointeur vers une mémoire tampon destinée à recevoir une chaîne terminée par le caractère NULL qui spécifie l’identité d’application complète retournée.|LPWSTR|
|`pdwIdentityBufferLength`|Pointeur vers une valeur DWORD qui est la longueur de la `pwzApplicationIdentity` mémoire tampon, en WCHARs. Cela comprend l’espace pour le caractère de fin NULL.|LPDWORD|
|`pwzProcessorArchitecture`|Pointeur vers une mémoire tampon destinée à recevoir une chaîne terminée par le caractère NULL qui spécifie l’architecture du processeur du déploiement de l’application, à partir du manifeste.|LPWSTR|
|`pdwArchitectureBufferLength`|Pointeur vers une valeur DWORD qui est la longueur de la `pwzProcessorArchitecture` mémoire tampon, en WCHARs.|LPDWORD|
|`pwzApplicationManifestCodebase`|Pointeur vers une mémoire tampon destinée à recevoir une chaîne terminée par le caractère NULL qui spécifie le code base du manifeste d’application, à partir du manifeste.|LPWSTR|
|`pdwCodebaseBufferLength`|Pointeur vers une valeur DWORD qui est la longueur de la `pwzApplicationManifestCodebase` mémoire tampon, en WCHARs.|LPDWORD|
|`pwzDeploymentProvider`|Pointeur vers une mémoire tampon destinée à recevoir une chaîne terminée par le caractère NULL qui spécifie le fournisseur de déploiement du manifeste, le cas échéant. Dans le cas contraire, une chaîne vide est retournée.|LPWSTR|
|`pdwProviderBufferLength`|Pointeur vers une valeur DWORD qui correspond à la longueur de `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>Valeur retournée
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Retourne HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) si une mémoire tampon est trop petite.

### <a name="remarks"></a>Notes
 Les pointeurs ne doivent pas avoir la valeur null. `pcwzActivationUrl` et `pcwzPathToDeploymentManifest` ne doivent pas être vides.

 L’appelant est responsable du nettoyage de l’URL d’activation. Par exemple, l’ajout de caractères d’échappement lorsqu’ils sont nécessaires ou la suppression de la chaîne de requête.

 Il incombe à l’appelant de limiter la longueur d’entrée. Par exemple, la longueur maximale de l’URL est de 2 Ko.

## <a name="launchapplication"></a>LaunchApplication
 Lance ou installe une application à l’aide d’une URL de déploiement.

### <a name="parameters"></a>Paramètres

|Paramètre|Description|Type|
|---------------|-----------------|----------|
|`deploymentUrl`|Pointeur vers une chaîne se terminant par un caractère NULL qui contient l’URL du manifeste de déploiement.|LPCWSTR|
|`data`|Réservé à un usage ultérieur. Doit être NULL.|LPVOID|
|`flags`|Réservé à un usage ultérieur. Doit être égal à 0.|DWORD|

### <a name="return-value"></a>Valeur retournée
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Voir aussi
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>