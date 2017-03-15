---
title: "ClickOnce Unmanaged API Reference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "LaunchApplication [ClickOnce unmanaged]"
  - "ClickOnce, unmanaged APIs"
  - "CleanOnlineAppCache [ClickOnce unmanaged]"
  - "CleanOnlineAppCacheW interface [ClickOnce unmanaged]"
  - "GetDeploymentDataFromManifest [ClickOnce unmanaged]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 6
---
# ClickOnce Unmanaged API Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

API [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publiques non managées de dfshim.dll.  
  
## CleanOnlineAppCache  
 Nettoie ou désinstalle toutes les applications en ligne du cache de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Valeur de retour  
 En cas de succès, retourne S\_OK ; sinon, retourne un HRESULT qui représente l'anomalie.  Si une exception managée se produit, la méthode retourne 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
### Remarques  
 L'appel de CleanOnlineAppCache démarrera le service [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], s'il n'est pas déjà en route.  
  
## GetDeploymentDataFromManifest  
 Récupère des informations de déploiement du manifeste et de l'URL d'activation.  
  
### Paramètres  
  
|Paramètre|Description|Type|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Pointeur vers le `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Pointeur vers le `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Un pointeur vers une mémoire tampon, destinée à recevoir une chaîne terminée par le caractère NULL spécifiant l'identité retournée complète de l'application.|LPWSTR|  
|`pdwIdentityBufferLength`|Un pointeur vers un DWORD qui est la longueur de la mémoire tampon `pwzApplicationIdentity`, en WCHAR.  Cela inclut l'espace pour le caractère NULL de fin.|LPDWORD|  
|`pwzProcessorArchitecture`|Un pointeur vers une mémoire tampon, destinée à recevoir une chaîne terminée par le caractère NULL qui spécifie l'architecture du processeur du déploiement de l'application depuis le manifeste.|LPWSTR|  
|`pdwArchitectureBufferLength`|Un pointeur vers un DWORD qui est la longueur de la mémoire tampon `pwzProcessorArchitecture`, en WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Un pointeur vers une mémoire tampon destinée à recevoir une chaîne terminée par le caractère NULL qui spécifie le code base du manifeste de l'application, depuis le manifeste.|LPWSTR|  
|`pdwCodebaseBufferLength`|Un pointeur vers un DWORD qui est la longueur de la mémoire tampon `pwzApplicationManifestCodebase`, en WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Un pointeur vers une mémoire tampon destinée à recevoir une chaîne terminée par le caractère NULL qui spécifie le fournisseur de déploiement du manifeste, s'il est présent.  Dans le cas contraire, une chaîne vide est retournée.|LPWSTR|  
|`pdwProviderBufferLength`|Un pointeur vers un DWORD qui est la longueur du `pwzProviderBufferLength`.|LPDWORD|  
  
### Valeur de retour  
 En cas de succès, retourne S\_OK ; sinon, retourne un HRESULT qui représente l'anomalie.  Retourne HRESULTFROMWIN32 \(ERROR\_INSUFFICIENT\_BUFFER\) si la mémoire tampon est trop petite.  
  
### Remarques  
 Les pointeurs ne doivent pas avoir la valeur null.  `pcwzActivationUrl` et `pcwzPathToDeploymentManifest` ne doivent pas être vides.  
  
 C'est la responsabilité de l'appelant de nettoyer l'URL d'activation.  Par exemple, ajouter les caractères d'échappement là où ils sont exigés ou supprimer la chaîne de requête.  
  
 C'est la responsabilité de l'appelant de limiter la longueur d'entrée.  Par exemple, la longueur maximale de l'URL est 2 Ko.  
  
## LaunchApplication  
 Lance ou installe une application en utilisant une URL de déploiement.  
  
### Paramètres  
  
|Paramètre|Description|Type|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Pointeur vers une chaîne terminée par le caractère NULL qui contient l'URL du manifeste de déploiement.|LPCWSTR|  
|`data`|Réservé à une utilisation future.  Doit être NULL.|LPVOID|  
|`flags`|Réservé à une utilisation future.  Doit être 0.|DWORD|  
  
### Valeur de retour  
 En cas de succès, retourne S\_OK ; sinon, retourne un HRESULT qui représente l'anomalie.  Si une exception managée se produit, la méthode retourne 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
## Voir aussi  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>