# Java-Mail-Sample
		// No Authentication
		Properties props = System.getProperties();
	        props.put("mail.smtp.host", "192.168.1.214");

	        Session session = Session.getInstance(props, null);
	        Transport tr = session.getTransport("smtp");
	        tr.connect(session.getProperty("mail.smtp.host"), session.getProperty("mail.smtp.user"),    session.getProperty("mail.smtp.password"));

	        Message msg = new MimeMessage(session);
	        msg.setFrom(new InternetAddress("generali@ddd.com"));
	        msg.setSentDate(new Date());
	        msg.addRecipient(Message.RecipientType.TO, new InternetAddress("pratyay@generali.co.th"));
	        msg.setSubject("Test"); 
	        msg.setContent("<b>hello<b>", "text/html; charset=TIS-620");

	        msg.saveChanges();
	        tr.sendMessage(msg, msg.getAllRecipients());
	        tr.close();
		
		// Authentication
		final String username = "barofhxz";
		final String password = "k7A!z5PN";

		Properties props = new Properties();
		props.put("mail.smtp.auth", "true");
		props.put("mail.smtp.starttls.enable", "true");
		props.put("mail.smtp.host", "202.129.16.74");
		props.put("mail.smtp.port", "587");

		Session session = Session.getInstance(props,
		  new javax.mail.Authenticator() {
			protected PasswordAuthentication getPasswordAuthentication() {
				return new PasswordAuthentication(username, password);
			}
		  });

		try {

			Message message = new MimeMessage(session);
			message.setFrom(new InternetAddress("from-email@gmail.com"));
			message.setRecipients(Message.RecipientType.TO,
				InternetAddress.parse("pratya@hotmail.com"));
			message.setSubject("Testing Subject");
			message.setText("Dear Mail Crawler,"
				+ "\n\n No spam to my email, please!");

			Transport.send(message);

			System.out.println("Done");

		} catch (MessagingException e) {
			throw new RuntimeException(e);
		}
		

# Spring Mail
		JavaMailSenderImpl mailSender = new JavaMailSenderImpl();
	        mailSender.setHost("192.168.1.214");
	        mailSender.setPort(25);
	         
	        MimeMessage message = mailSender.createMimeMessage();
	        
	        MimeMessageHelper helper = new MimeMessageHelper(message, true);
	        helper.setFrom("xxxxx@generali.co.th");
	        helper.setTo("pratyay@generali.co.th");
	        helper.setSubject("ssssssssssss");
	        helper.setText("sssssssss");
	        mailSender.send(message);
