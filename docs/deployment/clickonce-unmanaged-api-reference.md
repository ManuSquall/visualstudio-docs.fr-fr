---
title: Référence des API non managées ClickOnce | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900270"
---
# <a name="clickonce-unmanaged-api-reference"></a>Informations de référence sur les API non managées ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API publiques non managées de dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Nettoie ou désinstalle toutes les applications en ligne à partir de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache d’application.

### <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0 x 80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Notes
 Appel de CleanOnlineAppCache démarrera le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] du service si elle n’est pas déjà en cours d’exécution.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Récupère des informations sur le déploiement à partir de l’URL du manifeste et l’activation.

### <a name="parameters"></a>Paramètres

|Paramètre|Description|Type|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Un pointeur vers le `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Un pointeur vers le `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Un pointeur vers une mémoire tampon pour recevoir une chaîne se terminant par NULL qui spécifie l’identité de l’application complète est retourné.|LPWSTR|
|`pdwIdentityBufferLength`|Un pointeur vers une valeur DWORD qui est la longueur de la `pwzApplicationIdentity` mémoire tampon, en WCHAR. Cela inclut l’espace pour le caractère NULL de fin.|LPDWORD|
|`pwzProcessorArchitecture`|Un pointeur vers une mémoire tampon pour recevoir une chaîne se terminant par NULL qui spécifie l’architecture du processeur du déploiement d’application, à partir du manifeste.|LPWSTR|
|`pdwArchitectureBufferLength`|Un pointeur vers une valeur DWORD qui est la longueur de la `pwzProcessorArchitecture` mémoire tampon, en WCHAR.|LPDWORD|
|`pwzApplicationManifestCodebase`|Un pointeur vers une mémoire tampon pour recevoir une chaîne se terminant par NULL qui spécifie la base de code du manifeste d’application, à partir du manifeste.|LPWSTR|
|`pdwCodebaseBufferLength`|Un pointeur vers une valeur DWORD qui est la longueur de la `pwzApplicationManifestCodebase` mémoire tampon, en WCHAR.|LPDWORD|
|`pwzDeploymentProvider`|Un pointeur vers une mémoire tampon pour recevoir une chaîne se terminant par NULL qui spécifie le fournisseur de déploiement à partir du manifeste, s’il est présent. Sinon, une chaîne vide est retournée.|LPWSTR|
|`pdwProviderBufferLength`|Un pointeur vers une valeur DWORD qui est la longueur de la `pwzProviderBufferLength`.|LPDWORD|

### <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Retourne HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) si une mémoire tampon est trop petite.

### <a name="remarks"></a>Notes
 Les pointeurs ne doivent pas être null. `pcwzActivationUrl` et `pcwzPathToDeploymentManifest` ne doit pas être vide.

 Il est responsable de l’appelant pour nettoyer l’URL d’activation. Par exemple, ajout d’échappement des caractères lorsqu’ils sont nécessaires ou la suppression de la chaîne de requête.

 Il est responsable de l’appelant pour limiter la longueur d’entrée. Par exemple, la longueur maximale des URL est de 2 Ko.

## <a name="launchapplication"></a>LaunchApplication
 Lance ou installe une application à l’aide d’une URL de déploiement.

### <a name="parameters"></a>Paramètres

|Paramètre|Description|Type|
|---------------|-----------------|----------|
|`deploymentUrl`|Un pointeur vers une chaîne se terminant par NULL qui contient l’URL du manifeste de déploiement.|LPCWSTR|
|`data`|Réservé à un usage ultérieur. Doit être NULL.|LPVOID|
|`flags`|Réservé à un usage ultérieur. Doit être 0.|DWORD|

### <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0 x 80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Voir aussi
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>