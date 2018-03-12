---
title: "Référence des API non managées ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: cplusplus
ms.openlocfilehash: 392ada2288adcc229834f617c2f6284bb2e7ed0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>Référence des API non managées ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]API publiques non managées de dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Nettoie ou désinstalle toutes les applications en ligne à partir de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache de l’application.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0 x 80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Notes  
 Appel de CleanOnlineAppCache démarrera le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] si elle n’est pas déjà en cours d’exécution du service.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Récupère les informations de déploiement à partir de l’URL du manifeste et l’activation.  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|Type|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Un pointeur vers le `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Un pointeur vers le `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Pointeur vers une mémoire tampon pour recevoir une chaîne se terminant par NULL qui spécifie l’identité de l’application complète est retourné.|LPWSTR|  
|`pdwIdentityBufferLength`|Un pointeur vers un DWORD qui est la longueur de la `pwzApplicationIdentity` mémoire tampon, en WCHAR. Cela inclut l’espace pour le caractère NULL de fin.|LPDWORD|  
|`pwzProcessorArchitecture`|Pointeur vers une mémoire tampon pour recevoir une chaîne se terminant par NULL qui spécifie l’architecture du processeur du déploiement d’application, à partir du manifeste.|LPWSTR|  
|`pdwArchitectureBufferLength`|Un pointeur vers un DWORD qui est la longueur de la `pwzProcessorArchitecture` mémoire tampon, en WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Pointeur vers une mémoire tampon pour recevoir une chaîne se terminant par NULL qui spécifie le code base du manifeste d’application, à partir du manifeste.|LPWSTR|  
|`pdwCodebaseBufferLength`|Un pointeur vers un DWORD qui est la longueur de la `pwzApplicationManifestCodebase` mémoire tampon, en WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Un pointeur vers une mémoire tampon pour recevoir une chaîne terminée par le caractère NULL qui spécifie le fournisseur de déploiement à partir du manifeste, le cas échéant. Sinon, une chaîne vide est retournée.|LPWSTR|  
|`pdwProviderBufferLength`|Un pointeur vers un DWORD qui est la longueur de la `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Retourne HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) si une mémoire tampon est trop petite.  
  
### <a name="remarks"></a>Notes  
 Les pointeurs ne doivent pas être null. `pcwzActivationUrl`et `pcwzPathToDeploymentManifest` ne doit pas être vide.  
  
 Il est responsable de l’appelant pour nettoyer l’URL d’activation. Par exemple, ajout d’échappement des caractères lorsqu’ils sont nécessaires ou la suppression de la chaîne de requête.  
  
 Il est responsable de l’appelant pour limiter la longueur d’entrée. Par exemple, la longueur maximale des URL est 2 Ko.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Lance ou installe une application à l’aide d’une URL de déploiement.  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|Type|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Pointeur vers une chaîne terminée par le caractère NULL qui contient l’URL du manifeste de déploiement.|LPCWSTR|  
|`data`|Réservé à un usage ultérieur. Doit être NULL.|LPVOID|  
|`flags`|Réservé à un usage ultérieur. Doit être 0.|DWORD|  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0 x 80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>