# Custom Forms

 Place the following above a HTML form.

    <?php
    if (!empty($_POST)) {
        global $siteData, $siteDefineData;
        require_once ENV_ROOT.'/portal/libraries/formLogger.api.php';
        $logger = new formLoggerApi();
        $logger->setSiteId($siteData['site.id']);
        $logger->setSessionId($siteDefineData['cms_tracking_sessions']['session.id']);
        $logger->setFormId('form_logger_');
        $logger->setFormName('Form Name');
        $logger->setNotificationEmailAddresses('john@john.com');    
        if ($logger->saveData($_POST)) {
            echo '<h1>Thank you!!</h1>';
            echo '<p>Extra content?</p>';
        } else {
            echo '<h1>It looks like something went wrong.</h1>';
        }
    }
    ?>

For your form you need to name your inputs "form_logger_" , any from inputs should be named accordingly.

For example, '<input name="form_logger_first_name" />' 


    <form action="" post>
      <input name="form_logger_first_name" />
      <label>First Name</label>
    </form>
