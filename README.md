Tapestry CSRF Protection
========================

[![Build Status](https://travis-ci.org/porscheinformatik/tapestry-csrf-protection.png?branch=master)](https://travis-ci.org/porscheinformatik/tapestry-csrf-protection)

Cross-Site-Request-Forgery (CSRF) protection for Apache Tapestry 5.

## License

This software is licensed under the Apache Software License, Version 2.0, http://www.apache.org/licenses/LICENSE-2.0.txt

## Features

 - Protects all component event handler (like event links, forms, etc.) against CSRF
 - Adds CSRF token to all event links and adds hidden field with CSRF token to all form POSTs
 - Tokens are generated on a per-session basis

## Usage

Just add this module as a Maven (or Gradle or Ivy) dependency: 

	<dependency>
		<groupId>org.apache.tapestry</groupId>
		<artifactId>tapestry-csrf-protection</artifactId>
		<version>{tapstry-csrf.version}</version>
	</dependency>
	
If you have pages that should not be checked for CSRF token, then add the annotation @NotCsrfProtected.

	@NotCsrfProtected
	public class MyInsecurePage	
	{
		@Component
		private EventLink save;

		@OnEvent("save")
		void save() 
		{
			// this event handler is not protected
		}
	}