---
title: 'Comment : spécifier une URL de prise en charge pour les composants requis dans un déploiement ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679972"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Comment : spécifier une URL du support technique pour chaque composant requis lors d'un déploiement ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement peut tester un certain nombre de conditions préalables qui doivent être disponibles sur l’ordinateur client pour que l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application puisse s’exécuter. Il s’agit notamment de la version minimale requise du, de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] version du système d’exploitation et de tous les assemblys qui doivent être préinstallés dans le global assembly cache (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Toutefois, ne peut pas installer l’une de ces conditions préalables. Si un composant requis est introuvable, il interrompt simplement l’installation et affiche une boîte de dialogue qui explique pourquoi l’installation a échoué.  
  
 Il existe deux méthodes pour installer les composants requis. Vous pouvez les installer à l’aide d’une application de programme d’amorçage. Vous pouvez également spécifier une URL de support pour chaque composant requis, qui est affiché pour les utilisateurs de la boîte de dialogue si le composant requis est introuvable. La page référencée par cette URL peut contenir des liens vers des instructions pour l’installation de la configuration requise. Si une application ne spécifie pas d’URL de support pour un composant requis individuel, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] affiche l’URL de support spécifiée dans le manifeste de déploiement pour l’application dans son ensemble, si elle est définie.  
  
 Bien que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Mage.exe et MageUI.exe puissent tous être utilisés pour générer des [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiements, aucun de ces outils ne prend directement en charge la spécification d’une URL de support pour des composants requis individuels. Ce document décrit comment modifier le manifeste d’application et le manifeste de déploiement de votre déploiement pour inclure ces URL de prise en charge.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Spécification d’une URL de support pour un composant requis individuel  
  
1. Ouvrez le manifeste d’application (fichier. manifest) de votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application dans un éditeur de texte.  
  
2. Pour un composant requis du système d’exploitation, ajoutez l' `supportUrl` attribut à l' `dependentOS` élément :  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Pour un composant requis pour une certaine version du common language runtime, ajoutez l' `supportUrl` attribut à l' `dependentAssembly` entrée qui spécifie la dépendance de Common Language Runtime :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Pour un composant requis pour un assembly qui doit être préinstallé dans le Global Assembly Cache, définissez `supportUrl` pour l' `dependentAssembly` élément qui spécifie l’assembly requis :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. facultatif. Pour les applications qui ciblent le .NET Framework 4, ouvrez le manifeste de déploiement (le fichier. application) de votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application dans un éditeur de texte.  
  
6. Pour une condition préalable .NET Framework 4, ajoutez l' `supportUrl` attribut à l' `compatibleFrameworks` élément :  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Une fois que vous avez modifié manuellement le manifeste de l’application, vous devez signer à nouveau le manifeste de l’application à l’aide de votre certificat numérique, puis mettre à jour et signer à nouveau le manifeste de déploiement. Vous devez utiliser les outils du kit de développement logiciel (SDK) Mage.exe ou MageUI.exe pour effectuer cette tâche, car la régénération de ces fichiers à l’aide de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] efface vos modifications manuelles. Pour plus d’informations sur l’utilisation de Mage.exe pour signer à nouveau les manifestes, consultez [Comment : signer à nouveau des manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 L’URL de support n’est pas affichée dans la boîte de dialogue si l’application est marquée pour s’exécuter en confiance partielle.  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (Outil Manifest Generation and Editing)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Appartient](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Conditions préalables pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)
