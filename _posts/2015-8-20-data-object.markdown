---
layout: post
title:  "Data object in Ruby"
date:   2015-08-20 13:06:27
categories: Ruby
---

1. Struct

    `Email = Struct.new(:from, :to, :subject, :body)`

    Or:

        Email = Struct.new(:from, :to, :subject, :body) do
        ...
        end

2. Virtus gem:

        class User
          include Virtus.model

          attribute :email, String
          attribute :verified, Boolean, default: false
          attribute :created_at, Time
        end
