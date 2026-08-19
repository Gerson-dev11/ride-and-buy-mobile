# Ride & Buy Mobile

![Flutter](https://img.shields.io/badge/Flutter-3.22.0-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![PostgREST](https://img.shields.io/badge/PostgREST-FF4F00?style=for-the-badge)
![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![AWS Rekognition](https://img.shields.io/badge/AWS%20Rekognition-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Azure AI](https://img.shields.io/badge/Azure%20AI-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Wompi](https://img.shields.io/badge/Wompi-00AEEF?style=for-the-badge)
![SendGrid](https://img.shields.io/badge/SendGrid-1A82E2?style=for-the-badge&logo=twilio&logoColor=white)
![Material Design](https://img.shields.io/badge/Material%20Design-757575?style=for-the-badge&logo=material-design&logoColor=white)

---

Aplicación móvil de renta de automóviles desarrollada con Flutter y Dart. Utiliza la ubicación del usuario para encontrar negocios de renta cercanos dentro de un radio de 30 km, permitiendo descubrir vehículos disponibles sin necesidad de conocer previamente las direcciones de los locales. Centraliza el proceso completo de renta en una única interfaz móvil.

---

## Descripción General

Proyecto desarrollado como parte de una iniciativa de software. No se encuentra desplegado como producto comercial y los servicios backend originales no están activos actualmente. El repositorio puede descargarse y revisarse, y las interfaces pueden explorarse tras realizar las configuraciones necesarias.

---

## Funcionalidades Principales

- Búsqueda basada en ubicación de negocios de renta en un radio de 30 km
- Exploración y filtrado de vehículos por precio y tipo
- Vista detallada de vehículos con efecto Parallax
- Flujo completo de renta con selección de fechas
- Procesamiento de pagos mediante Wompi
- Generación y escaneo de códigos QR para validación de entregas y devoluciones
- Autenticación en dos pasos con verificación de identidad
- Roles de usuario (Cliente y Administrador)
- Panel administrativo para negocios de renta
- Publicación de vehículos con validación asistida por IA
- Lista de favoritos (demostrativa)
- Sección de notificaciones (demostrativa)

---

## Arquitectura

La aplicación implementa Clean Architecture para separar responsabilidades en capas:

- **Presentation**: Componentes de interfaz de usuario, widgets y gestión de estado
- **Domain**: Lógica de negocio, entidades y casos de uso
- **Data**: Implementaciones de repositorios, fuentes de datos y modelos
- **Backend/API Communication**: Comunicación con la API PostgREST
- **External Services**: Autenticación, pagos, servicios de IA, envío de correos

Esta separación mantiene la lógica de negocio desacoplada de la interfaz de usuario y de las implementaciones de servicios externos, mejorando la mantenibilidad y la capacidad de prueba.

Arquitectura y Distribución:
```
📦lib
 ┣ 📂App
 ┃ ┣ 📂DATA
 ┃ ┃ ┣ 📂datasources
 ┃ ┃ ┃ ┣ 📂Auth
 ┃ ┃ ┃ ┃ ┣ 📜IADocument_DataSourcers.dart
 ┃ ┃ ┃ ┃ ┣ 📜rentas_remote_datasource.dart
 ┃ ┃ ┃ ┃ ┗ 📜vehicle_remote_datasource.dart
 ┃ ┃ ┃ ┗ 📂Chat
 ┃ ┃ ┃ ┃ ┗ 📜chat_remote_datasource.dart
 ┃ ┃ ┣ 📂models
 ┃ ┃ ┃ ┣ 📂Auth
 ┃ ┃ ┃ ┃ ┣ 📜AuthProfilePendingUser_Model.dart
 ┃ ┃ ┃ ┃ ┣ 📜AuthProfilesUser_Model.dart
 ┃ ┃ ┃ ┃ ┗ 📜IADocumentAnalisis_Model.dart
 ┃ ┃ ┃ ┣ 📂Chat
 ┃ ┃ ┃ ┃ ┣ 📜chat_conversation_model.dart
 ┃ ┃ ┃ ┃ ┗ 📜chat_message_model.dart
 ┃ ┃ ┃ ┣ 📜Empresas_model.dart
 ┃ ┃ ┃ ┣ 📜RentaClienteModel.dart
 ┃ ┃ ┃ ┣ 📜rentas_model.dart
 ┃ ┃ ┃ ┣ 📜USERRENT_MODEL.dart
 ┃ ┃ ┃ ┗ 📜Vehiculo_model.dart
 ┃ ┃ ┗ 📂repositories
 ┃ ┃ ┃ ┣ 📂Auth
 ┃ ┃ ┃ ┃ ┣ 📜IADocumentAnalisis_RepositoryData.dart
 ┃ ┃ ┃ ┃ ┗ 📜ProfileUser_RepositoryData.dart
 ┃ ┃ ┃ ┣ 📂Chat
 ┃ ┃ ┃ ┃ ┗ 📜chat_repository_data.dart
 ┃ ┃ ┃ ┣ 📜EmpresaRepository_data.dart
 ┃ ┃ ┃ ┣ 📜rentas_repository_data.dart
 ┃ ┃ ┃ ┗ 📜vehicle_repository_data.dart
 ┃ ┣ 📂DOMAIN
 ┃ ┃ ┣ 📂Entities
 ┃ ┃ ┃ ┣ 📂Auth
 ┃ ┃ ┃ ┃ ┣ 📜aws_rekognition_result.dart
 ┃ ┃ ┃ ┃ ┣ 📜biometric_verify.dart
 ┃ ┃ ┃ ┃ ┣ 📜documentos_entity.dart
 ┃ ┃ ┃ ┃ ┣ 📜IADocumentAnalisis_Entities.dart
 ┃ ┃ ┃ ┃ ┣ 📜PROFILE_user_entity.dart
 ┃ ┃ ┃ ┃ ┗ 📜REGISTER_PENDING_user_entity.dart
 ┃ ┃ ┃ ┣ 📂Chat
 ┃ ┃ ┃ ┃ ┣ 📜chat_conversation_entity.dart
 ┃ ┃ ┃ ┃ ┗ 📜chat_message_entity.dart
 ┃ ┃ ┃ ┣ 📜auditlog_entity.dart
 ┃ ┃ ┃ ┣ 📜empresas_entity.dart
 ┃ ┃ ┃ ┣ 📜gobierno_verify_entity.dart
 ┃ ┃ ┃ ┣ 📜inspecion_vehicle_entity.dart
 ┃ ┃ ┃ ┣ 📜observacion_vehicle_entity.dart
 ┃ ┃ ┃ ┣ 📜pagos_entity.dart
 ┃ ┃ ┃ ┣ 📜rentas_entity.dart
 ┃ ┃ ┃ ┣ 📜reviews_entity.dart
 ┃ ┃ ┃ ┣ 📜sucursales_entity.dart
 ┃ ┃ ┃ ┣ 📜VEHICLE_ENTITY.dart
 ┃ ┃ ┃ ┣ 📜vehicle_telemetria_entity.dart
 ┃ ┃ ┃ ┣ 📜vehiculo_alerts_entity.dart
 ┃ ┃ ┃ ┗ 📜verification_sesions_entity.dart
 ┃ ┃ ┣ 📂repositories
 ┃ ┃ ┃ ┣ 📂Auth
 ┃ ┃ ┃ ┃ ┣ 📜IADocument_RepositoryDomain.dart
 ┃ ┃ ┃ ┃ ┗ 📜ProfileUser_RepositoryDomain.dart
 ┃ ┃ ┃ ┣ 📂Chat
 ┃ ┃ ┃ ┃ ┗ 📜chat_repository_domain.dart
 ┃ ┃ ┃ ┣ 📜EmpresaRepository_domain.dart
 ┃ ┃ ┃ ┣ 📜rentas_repository_domain.dart
 ┃ ┃ ┃ ┗ 📜vehicle_repository_domain.dart
 ┃ ┃ ┗ 📂usecases
 ┃ ┃ ┃ ┣ 📂Auth
 ┃ ┃ ┃ ┃ ┣ 📜Auth_UseCase.dart
 ┃ ┃ ┃ ┃ ┗ 📜IADocumentAnalisis_UseCases.dart
 ┃ ┃ ┃ ┣ 📂Renta
 ┃ ┃ ┃ ┃ ┣ 📜create_renta_usecase.dart
 ┃ ┃ ┃ ┃ ┣ 📜get_rentas_by_cliente_usecase.dart
 ┃ ┃ ┃ ┃ ┗ 📜get_rentas_by_empresa_usecase.dart
 ┃ ┃ ┃ ┣ 📜create_vehicle_usecase.dart
 ┃ ┃ ┃ ┣ 📜RegistrarEmpresa_UseCase.dart
 ┃ ┃ ┃ ┗ 📜search_vehicles_usecase.dart
 ┃ ┗ 📂presentation
 ┃ ┃ ┣ 📂pages
 ┃ ┃ ┃ ┣ 📂auth
 ┃ ┃ ┃ ┃ ┣ 📜AuthComplete.dart
 ┃ ┃ ┃ ┃ ┣ 📜AuthOtpPage.dart
 ┃ ┃ ┃ ┃ ┣ 📜AuthPage.dart
 ┃ ┃ ┃ ┃ ┣ 📜CameraCapturePage.dart
 ┃ ┃ ┃ ┃ ┣ 📜CameraSelfiePage.dart
 ┃ ┃ ┃ ┃ ┣ 📜PersonalDataForm.dart
 ┃ ┃ ┃ ┃ ┗ 📜UploadDocumentPage.dart
 ┃ ┃ ┃ ┗ 📂Home
 ┃ ┃ ┃ ┃ ┣ 📜Chat_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜Favoritos_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜HistoryAutos_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜Home_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜Notifications_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜payment_pending_screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜ProfileEmpresa.dart
 ┃ ┃ ┃ ┃ ┣ 📜ProfileSearchRent_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜ProfileUser_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜QRDevolucionScannerScreen.dart
 ┃ ┃ ┃ ┃ ┣ 📜QRScannerScreen.dart
 ┃ ┃ ┃ ┃ ┣ 📜RentVehicle_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜Seach_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜VehicleDetail_Screen.dart
 ┃ ┃ ┃ ┃ ┣ 📜VehiculosRENTADOS.dart
 ┃ ┃ ┃ ┃ ┣ 📜VEHICULOSSOLICITADOS.dart
 ┃ ┃ ┃ ┃ ┗ 📜VEHICULOS_EMPRESAS.dart
 ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┣ 📜camera_preview_box.dart
 ┃ ┃ ┃ ┣ 📜profile_screen_models.dart
 ┃ ┃ ┃ ┣ 📜profile_scroll_content.dart
 ┃ ┃ ┃ ┗ 📜profile_scroll_content_body.dart
 ┣ 📂Core
 ┃ ┣ 📂enums
 ┃ ┃ ┗ 📜enums.dart
 ┃ ┣ 📂errors
 ┃ ┃ ┗ 📜Auth_Exceptions.dart
 ┃ ┣ 📂sessions
 ┃ ┃ ┣ 📜session_manager copy.dart
 ┃ ┃ ┗ 📜session_manager.dart
 ┃ ┣ 📂utils
 ┃ ┃ ┣ 📜StaticsCacheService.dart
 ┃ ┃ ┣ 📜VehicleCacheService.dart
 ┃ ┃ ┗ 📜VehiculoRentadosCacheService.dart
 ┃ ┗ 📂widgets
 ┃ ┃ ┣ 📂AppBarWidget
 ┃ ┃ ┃ ┗ 📜CustomAppBarWidget.dart
 ┃ ┃ ┣ 📂Buttons
 ┃ ┃ ┃ ┗ 📜Button_global.dart
 ┃ ┃ ┣ 📂Cards
 ┃ ┃ ┃ ┣ 📜Card_CarsDetails.dart
 ┃ ┃ ┃ ┣ 📜Card_Optap.dart
 ┃ ┃ ┃ ┣ 📜CradBusiness.dart
 ┃ ┃ ┃ ┗ 📜EmpresWIdget.dart
 ┃ ┃ ┣ 📂CustomBottonBar
 ┃ ┃ ┃ ┗ 📜CustomBottonBar.dart
 ┃ ┃ ┣ 📂Heads
 ┃ ┃ ┃ ┗ 📜section_header_HomeWidgets.dart
 ┃ ┃ ┣ 📂inputs
 ┃ ┃ ┃ ┗ 📂home
 ┃ ┃ ┃ ┃ ┗ 📜search_field.dart
 ┃ ┃ ┣ 📂Modals
 ┃ ┃ ┃ ┣ 📜GlobalModalAction.widget.dart
 ┃ ┃ ┃ ┣ 📜GlobalModal_widget.dart
 ┃ ┃ ┃ ┣ 📜QRModal_Service.dart
 ┃ ┃ ┃ ┗ 📜QRScannerModal.dart
 ┃ ┃ ┣ 📂Photos
 ┃ ┃ ┃ ┗ 📜Photo_profil_global.dart
 ┃ ┃ ┣ 📂Reviews
 ┃ ┃ ┃ ┣ 📜Reviews_card.dart
 ┃ ┃ ┃ ┗ 📜Reviews_global.dart
 ┃ ┃ ┗ 📂ScaffoldWidget
 ┃ ┃ ┃ ┗ 📜CustomScaffoldWidget.dart
 ┣ 📂Feature
 ┃ ┣ 📂AUTH
 ┃ ┃ ┣ 📂Auht_Model
 ┃ ┃ ┃ ┗ 📜Auth_Model.dart
 ┃ ┃ ┣ 📂OTP
 ┃ ┃ ┃ ┗ 📜OTPForm.dart
 ┃ ┃ ┣ 📂widget
 ┃ ┃ ┃ ┣ 📜Auth_CustomButton_widget.dart
 ┃ ┃ ┃ ┣ 📜Auth_CustomTextField_widget.dart
 ┃ ┃ ┃ ┗ 📜Auth_SocialButton_widget.dart
 ┃ ┃ ┣ 📜Auth_Header.dart
 ┃ ┃ ┣ 📜Auth_LoginForm.dart
 ┃ ┃ ┣ 📜Auth_Registerform.dart
 ┃ ┃ ┗ 📜Auth_Tabs.dart
 ┃ ┣ 📂Form_Empresa
 ┃ ┃ ┣ 📜FORMEMPRESAS.dart
 ┃ ┃ ┣ 📜FORM_MODELO.dart
 ┃ ┃ ┗ 📜IMAGENES_SELECT.dart
 ┃ ┣ 📂Form_Vehiculo
 ┃ ┃ ┣ 📜FORM_VEHICULO.dart
 ┃ ┃ ┗ 📜VEHICLE_TEST_REAL.dart
 ┃ ┣ 📂Home
 ┃ ┃ ┣ 📂Chat
 ┃ ┃ ┃ ┗ 📂widget
 ┃ ┃ ┃ ┃ ┣ 📜Chat_Header_widget.dart
 ┃ ┃ ┃ ┃ ┣ 📜Chat_Message_widget.dart
 ┃ ┃ ┃ ┃ ┗ 📜Chat_Send_widget.dart
 ┃ ┃ ┣ 📂Favoritos
 ┃ ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┃ ┣ 📜FavoritosCard_widget.dart
 ┃ ┃ ┃ ┃ ┗ 📜FavoritosHeader_widget.dart
 ┃ ┃ ┣ 📂HISTORY_AUTOS
 ┃ ┃ ┃ ┣ 📂model
 ┃ ┃ ┃ ┃ ┗ 📜HistoryAutos_model.dart
 ┃ ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┃ ┣ 📜HistoryAutors_Card.dart
 ┃ ┃ ┃ ┃ ┗ 📜HistoryAutos_Tab.dart
 ┃ ┃ ┣ 📂HOME
 ┃ ┃ ┃ ┣ 📂Home_model
 ┃ ┃ ┃ ┃ ┗ 📜Home_Controller.dart
 ┃ ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┃ ┣ 📜Home_CardCars_widget.dart
 ┃ ┃ ┃ ┃ ┣ 📜Home_Promo_widget.dart
 ┃ ┃ ┃ ┃ ┣ 📜Home_SubHeader_widget.dart
 ┃ ┃ ┃ ┃ ┗ 📜Home_Welcome_widget.dart
 ┃ ┃ ┣ 📂Notifications
 ┃ ┃ ┃ ┗ 📂widget
 ┃ ┃ ┃ ┃ ┣ 📜Notification_Card_widget.dart
 ┃ ┃ ┃ ┃ ┣ 📜Notification_List_widget.dart
 ┃ ┃ ┃ ┃ ┗ 📜Notification_Tab_widget.dart
 ┃ ┃ ┣ 📂PROFILE_USER
 ┃ ┃ ┃ ┗ 📂widget
 ┃ ┃ ┃ ┃ ┣ 📜ProfileUser_Actions_widget.dart
 ┃ ┃ ┃ ┃ ┣ 📜ProfileUser_Header_widget.dart
 ┃ ┃ ┃ ┃ ┗ 📜ProfileUser_Information_widget.dart
 ┃ ┃ ┣ 📂Profle_Empresa
 ┃ ┃ ┃ ┗ 📂widget
 ┃ ┃ ┃ ┃ ┣ 📜GestionEmpresa.dart
 ┃ ┃ ┃ ┃ ┣ 📜ProfileButton.dart
 ┃ ┃ ┃ ┃ ┣ 📜ProfileEmpresaGanancias_widget.dart
 ┃ ┃ ┃ ┃ ┣ 📜ProfileEmpresaHeader_widget.dart
 ┃ ┃ ┃ ┃ ┗ 📜ProfleActions.dart
 ┃ ┃ ┗ 📂SEARCH
 ┃ ┃ ┃ ┣ 📂Search_model
 ┃ ┃ ┃ ┃ ┣ 📜Search_controller.dart
 ┃ ┃ ┃ ┃ ┗ 📜Search_model.dart
 ┃ ┃ ┃ ┗ 📂shared
 ┃ ┃ ┃ ┃ ┗ 📜Search_Header.dart
 ┃ ┣ 📂PAY_SUCCESS
 ┃ ┃ ┣ 📂widgets
 ┃ ┃ ┃ ┣ 📜Pay_AppBar_widget.dart
 ┃ ┃ ┃ ┣ 📜Pay_IconAnimation.dart
 ┃ ┃ ┃ ┣ 📜Pay_PrimaryButton_widget.dart
 ┃ ┃ ┃ ┣ 📜Pay_ResumeCard_widget.dart
 ┃ ┃ ┃ ┗ 📜Pay_SecondaryButton_widget.dart
 ┃ ┃ ┗ 📜Pay_Success_PRESENTATION.dart
 ┃ ┣ 📂PROFILE_RENT
 ┃ ┃ ┣ 📂widget
 ┃ ┃ ┃ ┣ 📜Profile_Content_widget.dart
 ┃ ┃ ┃ ┗ 📜Profile_Header_widget.dart
 ┃ ┃ ┣ 📜Profile_datos_model.dart
 ┃ ┃ ┗ 📜profile_model_model.dart
 ┃ ┣ 📂RENTAR_VEHICLE
 ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┣ 📜appbar_RentVehicleWidgets.dart
 ┃ ┃ ┃ ┣ 📜bottombar_RentVehicleDetails.dart
 ┃ ┃ ┃ ┣ 📜costSummaryCard_RentVehicleWidgets.dart
 ┃ ┃ ┃ ┣ 📜daySelector_RentVehicleWidgets.dart
 ┃ ┃ ┃ ┣ 📜detailCard_RentVehicleWidgets.dart
 ┃ ┃ ┃ ┣ 📜infoCard_RentVehicleWidgets.dart
 ┃ ┃ ┃ ┣ 📜paymentModal_RentVehicleWidgets.dart
 ┃ ┃ ┃ ┣ 📜timePickerField_RentVehicleWidgets.dart
 ┃ ┃ ┃ ┗ 📜timeSelection_RentVehicleWidgets.dart
 ┃ ┣ 📂VEHICLE_DETAIL
 ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┣ 📜VehicleDetail_AppBar_widget.dart
 ┃ ┃ ┃ ┣ 📜VehicleDetail_BackgroundImage_widget.dart
 ┃ ┃ ┃ ┣ 📜VehicleDetail_BottomBar_widget.dart
 ┃ ┃ ┃ ┣ 📜VehicleDetail_CardInfo_widget.dart
 ┃ ┃ ┃ ┣ 📜VehicleDetail_Description_widget.dart
 ┃ ┃ ┃ ┣ 📜VehicleDetail_Features_widget.dart
 ┃ ┃ ┃ ┣ 📜VehicleDetail_Info_widget.dart
 ┃ ┃ ┃ ┗ 📜VehicleDetail_Title_widget.dart
 ┃ ┗ 📂VERIFICACIONES
 ┃ ┃ ┣ 📂Coverage
 ┃ ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┃ ┗ 📜Coverage_Complete.dart
 ┃ ┃ ┗ 📂Error
 ┃ ┃ ┃ ┣ 📂ErrorPay
 ┃ ┃ ┃ ┃ ┗ 📜ErroPay.dart
 ┃ ┃ ┃ ┗ 📂widgets
 ┃ ┃ ┃ ┃ ┗ 📜Error_Auth.dart
 ┣ 📂flutter_flow
 ┃ ┣ 📜flutter_flow_animations.dart
 ┃ ┣ 📜flutter_flow_button_tabbar.dart
 ┃ ┣ 📜flutter_flow_drop_down.dart
 ┃ ┣ 📜flutter_flow_icon_button.dart
 ┃ ┣ 📜flutter_flow_model.dart
 ┃ ┣ 📜flutter_flow_theme.dart
 ┃ ┣ 📜flutter_flow_util.dart
 ┃ ┣ 📜flutter_flow_widgets.dart
 ┃ ┣ 📜form_field_controller.dart
 ┃ ┣ 📜keep_alive_wrapper.dart
 ┃ ┣ 📜lat_lng.dart
 ┃ ┣ 📜place.dart
 ┃ ┗ 📜uploaded_file.dart
 ┣ 📂Routers
 ┃ ┗ 📂router
 ┃ ┃ ┣ 📜MainComplete.dart
 ┃ ┃ ┗ 📜Routers.dart
 ┣ 📂Services
 ┃ ┣ 📂api
 ┃ ┃ ┣ 📜azure_validator_service.dart
 ┃ ┃ ┣ 📜s3_service.dart
 ┃ ┃ ┗ 📜woompi_pay_service.dart
 ┃ ┣ 📂render
 ┃ ┃ ┗ 📜render_db_client.dart
 ┃ ┗ 📂utils
 ┃ ┃ ┣ 📜EmpresasService.dart
 ┃ ┃ ┣ 📜ProfilesService.dart
 ┃ ┃ ┗ 📜QRService.dart
 ┣ 📜CreateTables.dart
 ┣ 📜deleteTables.dart
 ┣ 📜DROPTABLES.dart
 ┣ 📜getEmpresas.dart
 ┣ 📜index.dart
 ┣ 📜main.dart
 ┗ 📜main1.dart
```
---

## Autenticación y Verificación de Identidad

El flujo de autenticación incluye múltiples pasos de validación antes de conceder acceso:

1. Registro de usuario
2. Validación de correo electrónico con envío de OTP mediante SendGrid
3. Verificación del código OTP
4. Validación del DUI (documento de identidad)
5. Reconocimiento y verificación facial mediante AWS Rekognition
6. Activación de la cuenta
7. Inicio de sesión con segundo factor de autenticación
8. Persistencia de sesión mediante token almacenado localmente

El sistema implementa una capa adicional de verificación de identidad para garantizar un acceso seguro.

---

## Búsqueda por Ubicación

La aplicación utiliza la ubicación actual del dispositivo para descubrir negocios de renta dentro de un radio definido:

```
Ubicación del Usuario
      |
      v
Búsqueda de negocios de renta cercanos
      |
      v
Radio de 30 km
      |
      v
Locales de renta disponibles
      |
      v
Vehículos disponibles
```

---

## Flujo de Renta

El proceso principal de renta sigue el siguiente flujo:

```
Búsqueda de Vehículo
      |
      v
Detalle del Vehículo
      |
      v
Selección de fechas de renta
      |
      v
Especificación de duración
      |
      v
Información de la renta
      |
      v
Pago con Wompi
      |
      v
Validación del pago
      |
      +------------------+
      |                  |
      v                  v
   Exitoso             Fallido
      |                  |
      v                  v
Confirmación        Error de validación
```

---

## Integración de Pagos

Wompi se integra como proveedor de pagos con el siguiente flujo:

1. El usuario selecciona el vehículo y las fechas
2. Completa la información de la renta
3. Inicia el proceso de pago
4. Es redirigido al flujo de pago de Wompi
5. Retorna a la aplicación tras completar el pago
6. La aplicación valida el resultado del pago
7. Período máximo de validación de aproximadamente 2 minutos
8. Si el pago es exitoso, se genera la confirmación de la renta
9. Si el pago falla, no se confirma la renta y se muestra un error

La aplicación no considera una renta confirmada únicamente por haber iniciado el proceso de pago.

---

## Validación de Renta con QR

Tras completar una renta, el usuario puede consultar su renta activa, que incluye:

- Vehículo rentado
- Duración de la renta
- Estado de la renta
- Código QR asociado

Cuando el cliente llega al local, el administrador escanea el QR para validar la entrega. El mismo proceso se utiliza para la devolución del vehículo.

```
Pago Confirmado
       |
       v
Renta Activa
       |
       v
QR Generado
       |
       v
Cliente llega al local
       |
       v
Administrador escanea QR
       |
       v
Renta validada
```

---

## Roles de Usuario

Una misma persona puede actuar como:

- **Cliente**: Realiza búsquedas y rentas de vehículos
- **Administrador**: Gestiona un negocio de renta de vehículos

Un usuario puede registrarse como persona asociada a un local o empresa de renta y obtener capacidades administrativas sin necesidad de cuentas separadas.

---

## Panel Administrativo

El administrador dispone de un panel dentro de la aplicación que permite consultar:

- Vehículos rentados
- Vehículos actualmente en uso
- Vehículos disponibles
- Pagos recientes
- Rentas recién confirmadas
- Vehículos próximos a ser retirados
- Información operativa del negocio

El panel permite al administrador estar preparado cuando un cliente llega al local después de realizar una renta.

---

## Publicación de Vehículos

Los administradores pueden publicar nuevos vehículos a través de un proceso que incluye:

1. Proporcionar información del vehículo e imágenes
2. Validación asistida por servicios de inteligencia artificial
3. Verificación de parámetros establecidos
4. Aprobación o rechazo de la publicación

Si el vehículo no cumple con los parámetros establecidos, el proceso puede rechazar la publicación.

---

## Integración de Inteligencia Artificial

El proyecto utiliza servicios de IA para:

- Identificación de vehículos
- Identificación de placas
- Validación de información del automóvil
- Verificación de parámetros antes de publicar un vehículo

Servicios utilizados:

- **OpenAI**: Procesamiento y validación de información
- **Azure AI**: Identificación y verificación de vehículos

---

## Backend y Base de Datos

La aplicación utiliza:

- **PostgreSQL**: Base de datos relacional
- **PostgREST**: Capa API para interactuar con los datos
- **Render**: Infraestructura de despliegue

El backend gestiona información relacionada con:

- Usuarios
- Vehículos
- Locales
- Empresas
- Rentas
- Disponibilidad
- Pagos
- Roles
- Estados de las rentas

---

## Servicios Externos

### AWS
- Reconocimiento facial mediante AWS Rekognition
- Procesos de identificación y verificación

### SendGrid
- Envío de códigos OTP
- Verificación de correo electrónico

### Wompi
- Procesamiento de pagos de rentas

### OpenAI / Azure AI
- Identificación de vehículos
- Identificación de placas
- Validación de información de vehículos

---

## UI/UX

La aplicación utiliza **Material Design** como sistema visual con interfaces enfocadas en:

- Navegación móvil intuitiva
- Cards de vehículos con información clave
- Filtros y búsqueda
- Detalles de vehículos con efecto Parallax
- Formularios optimizados
- Información clara de renta
- Panel administrativo funcional
- Perfil de usuario
- Procesos de pago guiados
- Estados de reserva visuales

---

## Estructura del Proyecto

La estructura del proyecto sigue los principios de Clean Architecture. La organización de carpetas es conceptual y puede variar según la implementación específica:

```
lib/
├── presentation/     # UI components, screens, widgets, state management
├── domain/           # Entities, use cases, repository interfaces
├── data/             # Repository implementations, data sources, models
└── core/             # Utilities, constants, dependency injection
```

---

## Desafíos Técnicos

- Integración de múltiples servicios externos (AWS Rekognition, OpenAI, Azure AI, Wompi, SendGrid) manteniendo la lógica de negocio desacoplada
- Implementación de un flujo de autenticación con verificación de identidad en múltiples pasos
- Gestión de sesiones con autenticación en dos pasos y persistencia local de tokens
- Procesamiento de pagos con validación asíncrona y manejo de estados de transacción
- Generación y escaneo de códigos QR para validación de entregas y devoluciones
- Manejo de roles y permisos dentro de una misma aplicación
- Comunicación con API PostgREST desde una aplicación móvil
- Implementación de efectos visuales como Parallax en vistas de detalle

---

## Aprendizajes

El proyecto permitió adquirir experiencia práctica en:

- Desarrollo móvil con Flutter y Dart
- Implementación de Clean Architecture
- Comunicación con APIs REST
- PostgreSQL y PostgREST
- Integración backend
- Manejo de sesiones y autenticación
- Verificación de identidad y OTP
- Reconocimiento facial con AWS
- Integración de pagos con Wompi
- Geolocalización en aplicaciones móviles
- Generación y escaneo de códigos QR
- Manejo de roles y permisos
- Desarrollo de paneles administrativos
- Integración de servicios de inteligencia artificial
- Validación de vehículos con IA
- Manejo de diferentes estados de una renta

El proyecto también proporcionó una comprensión más profunda de cómo integrar múltiples servicios externos dentro de una misma aplicación manteniendo la lógica de negocio separada y bien organizada.

---

## Estado del Proyecto

Actualmente la aplicación:

- No está desplegada como producto comercial
- Los servicios originales no están completamente activos
- Fue desarrollada como proyecto de software
- El repositorio puede descargarse y revisarse
- Las interfaces pueden explorarse tras realizar las configuraciones necesarias
- Algunas funcionalidades dependientes del backend y servicios externos no pueden ejecutarse actualmente

---

## Repositorio

[https://github.com/Gerson-dev11/ride-and-buy-mobile](https://github.com/Gerson-dev11/ride-and-buy-mobile)

---

## Tecnologías Destacadas

El proyecto demuestra experiencia en:

- Flutter
- Clean Architecture
- Integración backend
- Autenticación
- Pagos
- Servicios de IA
- AWS
- Comunicación con bases de datos
- Geolocalización
- Flujos de trabajo con QR
- Funcionalidades basadas en roles
