---
title: 'Dépannage des Exceptions : System.ServiceModel.Security.MessageSecurityException | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6852b12e8a3cbc902770a2825d12697c12fc1760
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436550"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Dépannage des Exceptions : System.ServiceModel.Security.MessageSecurityException
Un <xref:System.ServiceModel.Security.MessageSecurityException> exception est levée lorsque [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] détermine qu’un message n’est pas correctement sécurisé ou qu’il a été falsifié. L'erreur se produit le plus fréquemment lorsque les conditions suivantes se vérifient toutes :  
  
- Vous utilisez une référence de service WCF via une connexion à distance telle qu'une connexion bureau à distance ou Terminal Services pour communiquer avec un service WCF (.svc) dans un projet de site Web ou d'application Web.  
  
- Vous ne possédez pas des autorisations d'administrateur sur le site distant.  
  
- Les demandes adressées à localhost sur le site distant sont gérées par le serveur de développement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
## <a name="associated-tips"></a>Conseils associés  
 **Résoudre les problèmes d’authentification NTLM lors de l’utilisation du serveur de développement ASP.Net.**  
 La sécurité de Stimulation/Réponse de Windows NT (NTLM) est généralement désactivée sur le serveur de développement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , ce qui permet l'accès anonyme. Par défaut, lorsque vous exécutez une session Terminal Services ou utilisez une connexion à distance, la sécurité NTLM est activée. Lorsque NTLM est activé, toutes les demandes adressées à localhost sont validées par rapport aux informations d'identification de l'utilisateur ou du processus qui a démarré le serveur de développement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Ceci réduit les menaces pour la sécurité. Toutefois, WCF exécute également sa propre authentification et n'autorise pas un compte non-administrateur à consommer des services WCF.  
  
 Si un utilisateur distant est susceptible d'exécuter le site Web à l'aide du serveur de développement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] et d'utiliser également un service Web ou WCF, vous pouvez créer une liaison de service personnalisée ou désactiver la sécurité NTLM.  
  
> [!IMPORTANT]
> Il n'est pas recommandé de désactiver la sécurité NTLM car cela pourrait constituer une menace pour la sécurité.  
  
 Si vous créez une liaison de service personnalisée, vous êtes encore protégé par l'authentification NTLM.  
  
 Effectuez les étapes suivantes pour créer une liaison de service personnalisée pour le service WCF.  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Pour créer une liaison de service personnalisée pour le service WCF hébergé dans le serveur de développement ASP.NET.  
  
1. Ouvrez le fichier Web.config pour le service WCF qui génère l'exception.  
  
2. Entrez les informations suivantes dans le fichier Web.config.  
  
   ```  
   <bindings>  
     <customBinding>  
       <binding name="Service1Binding">  
         <transactionFlow />  
         <textMessageEncoding />  
         <httpTransport authenticationScheme="Ntlm" />  
       </binding>  
     </customBinding>  
   </bindings>  
   ```  
  
3. Enregistrez et fermez le fichier Web.config.  
  
4. Dans le code du service Web ou WCF, modifiez la valeur du point de terminaison comme suit :  
  
   ```  
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
   ```  
  
    Ceci garantit que le service utilise la liaison personnalisée.  
  
5. Ajoutez une référence au service dans l'application Web qui accède au service. (Dans la boîte de dialogue **Ajouter une référence de service** , ajoutez une référence au service comme vous l'avez fait avec le service original qui générait l'exception.).  
  
   Vous pouvez suivre les étapes ci-dessous pour désactiver la sécurité NTLM lorsque vous utilisez une référence de service WCF.  
  
> [!IMPORTANT]
> Il n'est pas recommandé de désactiver la sécurité NTLM car cela pourrait constituer une menace pour la sécurité.  
  
#### <a name="to-turn-off-ntlm-security"></a>Pour désactiver la sécurité NTLM  
  
1. Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du site Web, puis cliquez sur **Pages de propriétés**.  
  
2. Sélectionnez **Options de démarrage**, puis désactivez la case à cocher **Authentification NTLM** .  
  
3. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Utiliser l’Assistant Exception](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)