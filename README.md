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
		
	
		

# Spring Mail
		JavaMailSenderImpl mailSender = new JavaMailSenderImpl();
	        mailSender.setHost("xxx.xxx.x.xxx");
	        mailSender.setPort(25);
	         
	        MimeMessage message = mailSender.createMimeMessage();
	        
	        MimeMessageHelper helper = new MimeMessageHelper(message, true);
	        helper.setFrom("xxxxx@generali.co.th");
	        helper.setTo("pratyay@generali.co.th");
	        helper.setSubject("ssssssssssss");
	        helper.setText("sssssssss");
	        mailSender.send(message);
