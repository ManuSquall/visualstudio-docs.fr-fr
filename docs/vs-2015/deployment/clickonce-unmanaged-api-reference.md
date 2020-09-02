---
title: Informations de référence sur les API non managées ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 714d7b18995bf1ad51b07e02227e440879f73c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192305"
---
# <a name="clickonce-unmanaged-api-reference"></a>Référence des API non managées ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] API publiques non managées à partir de dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Nettoie ou désinstalle toutes les applications en ligne du cache d' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
### <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Notes  
 L’appel de CleanOnlineAppCache démarre le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] service s’il n’est pas déjà en cours d’exécution.  
  
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
  
### <a name="return-value"></a>Valeur renvoyée  
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
  
### <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ; Sinon, retourne un HRESULT qui représente l’échec. Si une exception managée se produit, retourne 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>
